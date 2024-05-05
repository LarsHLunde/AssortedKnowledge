# Setting up Docker environment on Rocky 8
## Intro
I am planning on creating some of my own dockerized applications,  
due to finding the designs I find online to be over-built,  
under-built, outdated or straight-up nonfunctional.  

So I'm making a guide for making my own environment to run containers  
from scratch and I figured having a comprehensive guide to do so to be helpful.  

## Installing the basics
These are tools I see as the bare basics of an operation Debian environment:  
```
yum groupinstall -y "development tools"
yum install -y vim nano telnet nmap-ncat net-tools lsof dialog psmisc curl wget zip unzip yum-utils
```
Then give passwordless sudo to your user of choice:  
```
u=pyro
usermod -a -G sudo $u
echo "$u ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$u
```  
and turn off selinux:  
```
setenforce 0
sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config
```  
## Installing docker

First, remove the old packages that may be present:  
```  
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```  
then add the official repo:  
```  
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```  
and finally, run the install script:  
```  
yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```   
and enable the service:  
``` 
systemctl enable docker --now
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
