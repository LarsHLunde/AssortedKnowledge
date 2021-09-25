# How to create a local repo from the online repos with YUM
## Preface
This article will be going in to how to create a local repo,  
for patching offline systems and provide all the repo packages  
for offline installment and to avoid dependency hell.  
  
In the example we will be cloning the official Oracle Linux 7  
UEK6 and latest packages repos, with only the newest versions  
totaling about 5GB of data, which is about the same as the ISO  
however you will have all the official packages at your disposal  
instead of only the ones found on the DVD, and in the latest versions.  
  
The amount of repos needed and size of repos will vary by distribution,  
and version of distribution, but should work on:  
- Oracle Linux 6/7/8
- Redhat Linux 6/7/8
- Centos 6/7/8
- Fedora 6/7/8

## Preparations
For this excersice you will need 2 systems,  
one system, from here on called the seed system,  
to create the repository with and the deployment system  
that needs to be patched or install software.  
  
They should be as close as possible to eachother,  
if the system is a VM system, I suggest creating another VM  
but let it have an internet connection.  
If it's a cloud system, I suggest creating a seperate instance,  
with less resources but an internet connection, as they can be  
very different from the ones found on ISOs.  

## Creating the repo package
All work beyond this point assumes you are operating as root.  
After you have created your seed system we need to install  
yum-tools if it is not already included with the OS:  
```  
yum install -y yum-utils createrepo
```  
Then we need to see which repos are available to the system,  
this will vary by system, and you may not want to include all of them.  
```
[root@localhost ~]$ yum repolist
Loaded plugins: ulninfo
repo id                                                             repo name                                                                                                                           status
ol7_UEKR6/x86_64                                                    Latest Unbreakable Enterprise Kernel Release 6 for Oracle Linux 7Server (x86_64)                                                       413
ol7_latest/x86_64                                                   Oracle Linux 7Server Latest (x86_64)                                                                                                23,100
repolist: 23,513
```  
In our case there's only 2, and only one is essential, we will however include both.  
We will be creating a new folder at ```/repo``` to do all our work in.  

From here we need to sync all the repos we want to the repo folder, with the following commands:  
```  
reposync -l --newest-only --repoid=ol7_latest --download_path=/repo
reposync -l --newest-only --repoid=ol7_UEKR6 --download_path=/repo
```  
Adjusting the repoid's and amount for whatever is applicable for your system.  
Then we need to make the syncronized repos in to normal real repos,  
which mostly entails creating sqlite databases, metadata and versioning.  
```
createrepo /repo/ol7_latest/
createrepo /repo/ol7_UEKR6/
```  
Congratulations! You now have 2 full and completely working local repos!  
Now we need to zip it and ship it, or tar it because Oracle Linux 7  
does not come with unzip stock:  
```
cd /repo
tar -czvf updates.tar.gz ./*
```  
Sidenote, if you copy the repo folder to an apache or nginx public folder,  
you should be able to use it over that protocol, or even ftp.  
## Deploying the package
For this portion of the guide, we will be using ```/repo``` again.  
Transfer the tar.gz file over to your deployment system to /repo, and unpack:
```
cd /repo
tar xvf updates.tar.gz
```  
Then we need to disable all online, and therefore unusable, repos,  
as they will wait for timeout or make the system refuse to update at all.  
```
[root@localhost ~]$ yum repolist
Loaded plugins: ulninfo
repo id                                                             repo name                                                                                                                           status
ol7_UEKR6/x86_64                                                    Latest Unbreakable Enterprise Kernel Release 6 for Oracle Linux 7Server (x86_64)                                                       413
ol7_latest/x86_64                                                   Oracle Linux 7Server Latest (x86_64)                                                                                                23,100
repolist: 23,513
```  
find their coresponding repo files under ```/etc/yum.repos.d/```  
and set their enabled flag to 0, once you have done that for all repos,  
the repolist should return something like this:  
```
[root@localhost repo]# yum repolist
Loaded plugins: ulninfo
repolist: 0
```  
Then we create our own repo files in the same directory for our local repos:  
```
vi /etc/yum.repos.d/local-ol7.repo
```
```
[local-repo-ol7]
name=LocalOL7
baseurl=file:///repo/ol7_latest
enabled=1
gpgcheck=0
```  
```
vi /etc/yum.repos.d/local-uekr6.repo
```
```
[local-repo-uekr6]
name=LocalUEKR6
baseurl=file:///repo/ol7_UEKR6
enabled=1
gpgcheck=0
```  
Run repolist again to see that yum is happy with the changes:  
``` 
[root@localhost repo]# yum repolist
Loaded plugins: ulninfo
local-repo-ol7                                                                                                                                                                         | 2.9 kB  00:00:00
local-repo-uekr6                                                                                                                                                                       | 2.9 kB  00:00:00
(1/2): local-repo-uekr6/primary_db                                                                                                                                                     | 1.0 MB  00:00:00
(2/2): local-repo-ol7/primary_db                                                                                                                                                       | 4.5 MB  00:00:00
repo id                                                                                                repo name                                                                                        status
local-repo-ol7                                                                                         LocalOL7                                                                                         5,448
local-repo-uekr6                                                                                       LocalUEKR6                                                                                          85
repolist: 5,533
```  
We have a lot fewer packages this time, because we used the ```--newest-only``` flag,  
we cloning the repos, or the package would be 5-10 times bigger.  
  
You can now install any package like you had those repos online, without being online.  
Even really complex ones like this:  
[yum install -y oracle-database-preinstall-19c](resources/prereq_output.md)
  
or a full update:  
[yum update -y](resources/update_output.md)

Happy Linuxing  
