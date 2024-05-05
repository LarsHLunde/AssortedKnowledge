# How to set up offline repos for apt based systems
## Intro
**WARNING: This will require up to 1TB of storage**
For secure zones and closed off networks,  
where you may need to update from an offline source,
it is very useful to be able to clone and create your own.  
  
After a lot of experimentation, I found that it is not as easy  
as one might think, partially because the version of aptly and go  
supplied by the repos of most Debian based repos are outdated,  
so we need to install both of them from scratch.  
  
I will be cloning the repos of Ubuntu 22.04,  
and run the system inside a Ubuntu 22.04 Docker instance.  
There are 2 guides in here for creating Docker machines,  
but you can also set it up on a normal Ubuntu 22.04 machine/VM.  

## Creating the docker instance (if applicable)  
After creating a machine with a working Docker system,
create a basic Ubuntu 22.04 Docker instance to run the code from.  
You will also need a folder to save your repo to outside the Docker instance.  

Start by creating and building the image:  
```
mkdir aptly
cd aptly
echo 'FROM ubuntu:jammy' > Dockerfile
echo 'RUN apt-get update' >> Dockerfile
echo 'RUN echo "sleep infinity" > /init.sh' >> Dockerfile
echo 'ENTRYPOINT ["/bin/bash", "/init.sh"]' >> Dockerfile
docker build -t aptly .
```
Then run the following command with the folder linked to your host system:  
(you need to replace the part that says ```"$(pwd)"/aptly```)
```
docker run -d --name aptly -it --mount type=bind,source="$(pwd)"/aptly,target=/root/.aptly aptly
``` 
and now you can enter the Docker instance with:  
```
docker exec -it aptly /bin/bash
```  

## Installing the packages
Like mentioned before, we need to install a lot of things from scratch,  
but we start with the more normal packages:  
``` 
apt-get install -y git nano wget dialog build-essential screen 
```  
And then we move on to installing a newer version of Go:  
``` 
wget https://go.dev/dl/go1.21.6.linux-amd64.tar.gz
tar -xvf go1.21.6.linux-amd64.tar.gz -C /usr/local
echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.profile
source ~/.profile 
```  
and finally install aptly:  
```  
git clone https://github.com/aptly-dev/aptly
cd aptly
make modules install
``` 
then comes a bit of an annoying part,  
where you need to generate some keys for signing your own repos.
Just enter any name (but not empty), no email and write O for okay when prompted,  
and no password is needed, just press enter through the dialog.  
``` 
gpg --default-new-key-algo rsa4096 --gen-key --keyring pubring.gpg
``` 
then we add aptly to our path and generate the config file:  
```
echo "export PATH=$PATH:/root/go/bin" >> ~/.profile
source ~/.profile
aptly config show
```
You can edit the line ```"rootDir": "/root/.aptly"``` to suit your needs and space requirements,  
but if you are running docker, this would be the folder we linked earlier.  
  
We also need to link in the key we made earlier:  
```  
gpg --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg --export | gpg --no-default-keyring --keyring trustedkeys.gpg --import
``` 
  
If we check (and clean up) the repo list for the system, we see that there's not one,  
but 3 mirrors for Ubuntu 22.04, and they don't work well without eachother, so we need to do all 4:  
``` 
root@5911a505b913:/aptly# cat /etc/apt/sources.list | grep -v "#" | sort -t: -u

deb http://archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://archive.ubuntu.com/ubuntu/ jammy universe
deb http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ jammy-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ jammy-updates universe
deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted
deb http://security.ubuntu.com/ubuntu/ jammy-security multiverse
deb http://security.ubuntu.com/ubuntu/ jammy-security universe
```  
  
This is why this takes such a huge amount of space,  
we start by creating 4 mirrors in aptly:  
```
aptly -architectures="amd64" mirror create jammy-local http://archive.ubuntu.com/ubuntu/ jammy
aptly -architectures="amd64" mirror create jammy-backports-local http://archive.ubuntu.com/ubuntu/ jammy-backports
aptly -architectures="amd64" mirror create jammy-updates-local http://archive.ubuntu.com/ubuntu/ jammy-updates
aptly -architectures="amd64" mirror create jammy-security-local http://archive.ubuntu.com/ubuntu/ jammy-security
``` 
  
Now comes the first really time consuming part,  
and if you are somewhat adept at Linux,  
I suggest you use screen that we installed earlier.  
  
If not, best of luck.  We will start cloning the repos to disk.  
luckily this only takes a really long time the first time you run it.
If you want to test it as a concept, jammy-backports is by far the smallest:  
``` 
aptly mirror update jammy-local
aptly mirror update jammy-backports-local
aptly mirror update jammy-updates-local
aptly mirror update jammy-security-local
```  
As of 05.05.2024 the sizes are:  
| Repo | Size |
| --- | --- |
| jammy-local | 106G |
| jammy-backports | 1GB |
| jammy-updates | 240GB |
| jammy-security | 234GB |
  
The next step is to create the repo database files,  
which will also take a huge amount of time and is best run in a screen.  
This will take a moderate amount of time in the future instead of little time:  
```  
aptly snapshot create jammy-snapshot from mirror jammy-local
aptly snapshot create jammy-backports-snapshot from mirror jammy-backports-local
aptly snapshot create jammy-updates-snapshot from mirror jammy-updates-local
aptly snapshot create jammy-security-snapshot from mirror jammy-security-local
```
Finally we publish, which finalizes the repo (takes little time):  
```
aptly publish snapshot jammy-snapshot
aptly publish snapshot jammy-backports-snapshot
aptly publish snapshot jammy-updates-snapshot
aptly publish snapshot jammy-security-snapshot
```  
and if it's a local server that you want to serve, you serve:  
```
aptly serve -listen=:8080
```
And aptly will generate a source list for you.  
If you want to serve from local filesystem here's an example /etc/apt/sources.list file:  
```  
deb [trusted=yes] file:/repo/public jammy main restricted
deb [trusted=yes] file:/repo/public jammy universe
deb [trusted=yes] file:/repo/public jammy multiverse
deb [trusted=yes] file:/repo/public jammy main restricted
deb [trusted=yes] file:/repo/public jammy-backports main restricted universe multiverse
deb [trusted=yes] file:/repo/public jammy-updates main restricted
deb [trusted=yes] file:/repo/public jammy-updates multiverse
deb [trusted=yes] file:/repo/public jammy-updates universe
deb [trusted=yes] file:/repo/public jammy-security main restricted
deb [trusted=yes] file:/repo/public jammy-security multiverse
deb [trusted=yes] file:/repo/public jammy-security universe
```
