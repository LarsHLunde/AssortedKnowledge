# Rsync, a small guide and cheatsheet

Syntax of rsync: \
**rsync [OPTIONS] SRC DEST**

Common options : 

1. a : Archive mode : Copy recursively with permissions and all
2. v : Verbose : More informatione when transferring files
3. h : Human readable : Dynamically changes file transfer speeds and sizes to MB/GB/etc
4. z : Compress : Compress tranfer hopefully to save time and bytes
5. e : Specify remote shell : Used mostly for running rsync over ssh
7. P : Progress : Show progress, not the best, limited support
8. --del : Delete : Remove any files and folders in dest not on source side
9. --info=progress2 : Progress : Shows progress, looks better, better support


## Some examples
### Synchronize 2 folders :
```
rsync -avh /root/datafiles/ /backups/datafiles/
```
Everything in /root/datafiles/ will be put in /backups/datafiles/

### Synchronize folder in to a folder:
```
rsync -avh /root/datafiles /backups/datafiles/
```
Everything in /root/datafile will be copied in to /backups/datafiles/datafiles

### Rsync over ssh: 
```
rsync -avh -e ssh pyro@example.com:stuff/things ./
```
Everything in /home/pyro/stuff/things will be copied in to ./things

### Rsync over ssh with cert or other options: 
```
rsync -avh -e "ssh -i ./mycert" pyro@example.com:stuff/things ./
```
Everything in /home/pyro/stuff/things will be copied in to ./things
I've noticed in that some versions you have to use a modification:
```
rsync -avh -e "ssh -o IdentityFile=./mycert" pyro@example.com:stuff/things ./
```
But you can also add whatever other options you want to it, same syntax

### Rsync deleting old files
```
rsync -avh --del /root/datafiles/ /backups/datafiles/
``` 
Everything in /root/datafiles/ will be put in /backups/datafiles/ \
deleting all files and folders not on the source side.

## A word about compression
Compressing in-transit data is not only common, it's a wonderful idea. \
More sites that you probably realize use gzip compression to send website data to you.

In rsync, it uses the zip librar to compress data before sending it, \
and by default at a compression grade of 6, which is the linux default for the library.

This does however mean that for the duration of the transfer, the sending machine \
will have a core pinned to compress the data, and data will only be transferred as fast as it can compress.
In my testing, the throughput of the algorithm is somewhere between 20-30MB/s.

If you will not be trnasferring over that speed, you probably should use compression, \
if not, it will only make things slower.

I will do further testing on the subject, and make a matrix, \
but using compression is severely over represented in guides and examples online, \
and most networks can transfer well over 30MB/s.
