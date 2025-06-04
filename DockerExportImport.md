# How to create, export and import a docker instance
## Intro
You may be thinking, why would you want to do this?  
And the answer is simple, sometimes you will be working  
on an airgapped system, one with very restrictive firewalls,  
or even just inspecting firewalls messing up all the cert checks.  
  
In these cases, it's great to just make your own docker image locally,  
export it, compress it, upload it, import it and use it on a system  
that would otherwise not support the software.  
  
This has happened to me at least 4 times thusfar,
and because the procedure is a bit fiddly, I've decided to make a guide.  

## The export
For the example, we are going to use a very useful image I just created:  
https://github.com/LarsHLunde/docker-az-cli  
We follow the instructions and create the base configuration:  
```
git clone https://github.com/LarsHLunde/docker-az-cli.git  
cd docker-az-cli  
docker build -t az-cli .
docker run -d \
  --name az-cli \
  --restart unless-stopped \
  az-cli
```  
You will now have a running container ready for export.  
The first thing we need to do however, is get the entrypoint of the container,  
as this information does not survive the export process.  
Run the following command and save the result somewhere:  
```
root@debian:~/docker-az-cli# docker inspect -f '{{.Config.Entrypoint}}' az-cli
[/bin/bash /init.sh]
root@debian:~/docker-az-cli#
```   
Then we create the actual export:  
```
docker export az-cli -o az-cli.tar
```  
Optionally, we can compress the new export for transport:  
```
gzip -1 az-cli.tar
```  

## The import
If you, like me, are doing this on a test system with nothing important running on it,  
you can clear all the caches and non-running images by stopping az-cli and pruning the system:  
```
docker stop az-cli
docker system prune -af
```  
We start by un-gzipping the tarball, if you did gzip it:  
```
gunzip az-cli.tar.gz
```  
In order for the import to work, we need to add a change to the image while importing:  
**NB! THE SYNTAX IS VERY IMPORTANT**  
```
docker import --change 'ENTRYPOINT ["/bin/bash", "/init.sh"]' az-cli.tar az-cli
```  
and we can run the image like normal:  
```
 docker run -d \
  --name az-cli \
  --restart unless-stopped \
  az-cli
```  
