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
[root@localhost repo]# yum repolist
Loaded plugins: ulninfo
repo id           repo name                                                                    status
ol7_UEKR6/x86_64  Latest Unbreakable Enterprise Kernel Release 6 for Oracle Linux 7Server (x86    413
ol7_latest/x86_64 Oracle Linux 7Server Latest (x86_64)                                         23,100
repolist: 23,513

```  
In our case there's only 2, and only one is essential, we will however include both.  
We will be creating a new folder at ```/repo``` to do all our work in.  

From here we need to sync all the repos we want to the repo folder, with the following commands:  
```  
reposync -l --newest-only --repoid=ol7_latest --download_path=/repo
reposync -l --newest-only --repoid=ol7_UEKR6 --download_path=/repo
```  
on Oracle Linux 8  
I decided  to not include appstream repo,  
because even with newest it's over 40GB.  
```
reposync --newest-only --repoid=ol8_UEKR6 -p /repo
reposync --newest-only --repoid=ol8_baseos_latest -p /repo
```  
Adjusting the repoid's and amount for whatever is applicable for your system.  
Then we need to make the syncronized repos in to normal real repos,  
which mostly entails creating sqlite databases, metadata and versioning.  
```
createrepo /repo/ol7_latest/
createrepo /repo/ol7_UEKR6/
```  
on Oracle Linux 8  
```
createrepo /repo/ol8_baseos_latest/
createrepo /repo/ol8_UEKR6/
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
Loaded plugins: ulninfo
repo id           repo name                                                                    status
ol7_UEKR6/x86_64  Latest Unbreakable Enterprise Kernel Release 6 for Oracle Linux 7Server (x86    413
ol7_latest/x86_64 Oracle Linux 7Server Latest (x86_64)                                         23,100
repolist: 23,513
[root@localhost repo]#
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
repo id                                           repo name                                    status
local-repo-ol7                                    LocalOL7                                     5,448
local-repo-uekr6                                  LocalUEKR6                                      85
repolist: 5,533

```  
We have a lot fewer packages this time, because we used the ```--newest-only``` flag,  
when cloning the repos, or the package would be 5-10 times bigger.  
  
You can now install any package like you had those repos online, without being online.  
Even really complex ones like this:  
[yum install -y oracle-database-preinstall-19c](resources/prereq_output.md)
  
or a full update:  
[yum update -y](resources/update_output.md)

## Custom package setups
In some cases, you need to make custom repos,  
one good example of this is that cloning the entire Oracle Linux 8 appstream repo,  
or the EPEL repo, will simply take too much time and space to do in this fashion.  
  
In these cases, the easiest and best way to do so is by making a new custom repo.  
In this example I will be creating a repo just for ```oracle-database-preinstall-19c```,  
as it does not come with the baseos repo for Oracle Linux 8, but the appstream.  
Since the process seems to be a bit different on Oracle Linux 7,  
I will also do it with gparted from the EPEL repo.   
  
### Oracle Linux 8  
We start by creating a new repo folder called ol8_custom, with the same structure  
as the official repo clones use, and use yumdownloader to download all the packages.  
It was at this stage I ran in to a real complication, and concluded the best course  
of action is to just install the package on the seed system to make it easier  
and just reinstall all the packages or else you will need to make your own function for it:  

```
yum install -y yum-utils createrepo
mkdir -p /repo/ol8_custom/getPackage
yum install -y oracle-database-preinstall-19c
repoquery --requires --resolve --recursive oracle-database-preinstall-19c | xargs yum reinstall -y --downloadonly --downloaddir=/repo/ol8_custom/getPackage
```  
And you can do this for as many packages as you wish, there will be some duplicates between  
the baseos package and this custom package, but it will be fully resolved, releaving much headache.  
Then we just create a repo from it and zip it:  
```
createrepo /repo/ol8_custom/
cd /repo
tar -czvf updates.tar.gz ./*
```  
On the deployment system, I will disable all repos not the custom one,  
and install ```oracle-database-preinstall-19c```  

```
vi /etc/yum.repos.d/local-custom.repo
```
```
[local-repo-custom]
name=LocalCustom
baseurl=file:///repo/ol8_custom
enabled=1
gpgcheck=0
```  
And it works a treat : [yum install oracle-database-preinstall-19c](resources/custom_ol8.md)

### Oracle Linux 7
Was much more resilient to my atempts of making a custom repo,  
and after much tinkering I have concluded you need the whole base-repo with newest,  
like outlined at the start of the article, and then add on packages from other repos.  
  
As a direct consequence, no deployment package will be under 4.5-5GB,  
but we will take it from the top by installing dependencies, including EPEL:  
```
yum install -y yum-utils createrepo oracle-epel-release-el7
```  
and create the 2 base repos like we did previously:  
```  
reposync -l --newest-only --repoid=ol7_latest --download_path=/repo
reposync -l --newest-only --repoid=ol7_UEKR6 --download_path=/repo
```  
then we create the new repo folder and install our gparted package in download only mode  
```
mkdir -p /repo/ol7_custom/getPackage
yum install -y --downloadonly --downloaddir=/repo/ol7_custom/getPackage gparted
```  
then we create the repos and compress everything  
```
createrepo /repo/ol7_latest/
createrepo /repo/ol7_UEKR6/
createrepo /repo/ol7_custom/
cd /repo
tar -czvf updates.tar.gz ./*
```  
  
Transfer to deployment machine and untar
```
mdkir /repo
cd /repo
tar xvf updates.tar.gz
```  
and disable the other repos, and add the config files for the local ones.  
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
```
vi /etc/yum.repos.d/local-custom.repo
```
```
[local-repo-custom]
name=LocalCustom
baseurl=file:///repo/ol7_custom
enabled=1
gpgcheck=0
```  
Always double-check the ```yum repolist``` and we a off to the races:  
[yum install gparted](resources/custom_ol7.md)

Happy Linuxing  
