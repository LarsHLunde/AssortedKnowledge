# Setting up Docker environment on Debian 12
## Intro
I am planning on creating some of my own dockerized applications,  
due to finding the designs I find online to be over-built,  
under-built, outdated or straight-up nonfunctional.  

So I'm making a guide for making my own environment to run containers  
from scratch and I figured having a comprehensive guide to do so to be helpful.  

## Installing the basics
These are tools I see as the bare basics of an operation Debian environment:  
```
apt-get install -y sudo software-properties-common build-essential apt-utils vim nano telnet ncat net-tools iputils-ping policykit-1 lsof dialog psmisc systemd-cron curl p7zip-full zip unzip
```
Then give passwordless sudo to your user of choice:  
```
u=pyro
usermod -a -G sudo $u
echo "$u ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$u
```
 ## Installing docker

First, remove the old packages that may be present:  
```  
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```  
then add the official repo:  
```  
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```  
and finally, run the install script:  
```  
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```  
  
I also prefer having docker-compose installed:  
``` 
sudo apt-get install -y docker-compose
```  
and a couple of options I like for my instances:  
```
echo 'alias ll="ls -l"' >> /etc/bash.bashrc
```  

## Full reset
```  
cd 
rm -rf ./*
docker system prune -af
```  
Basic Ubuntu docker:  
```  
echo 'FROM ubuntu:latest' > Dockerfile
echo 'RUN apt-get update' >> Dockerfile
echo 'RUN echo "sleep infinity" > /init.sh' >> Dockerfile
echo 'ENTRYPOINT ["/bin/bash", "/init.sh"]' >> Dockerfile
``` 
Build something:  
```
git clone ...
cd ...
docker build -t application .
docker run -d -it application
```  

