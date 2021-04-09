# Rsync : Small guide, Benchmark and Cheatsheet

Syntax of rsync: \
**rsync [OPTIONS] SRC DEST**

Common options : 

1. a : Archive mode : Copy recursively with permissions and all
2. v : Verbose : More informatione when transferring files
3. h : Human readable : Dynamically changes file transfer speeds and sizes to MB/GB/etc
4. z : Compress : Compress tranfer hopefully to save time and bytes (more info later)
5. e : Specify remote shell : Used mostly for running rsync over ssh
7. P : Progress : Show progress, not the best, limited support
8. --del : Delete : Remove any files and folders in dest not on source side
9. --info=progress2 : Progress : Shows progress, looks better, better support
10. --compress-level=N : Compression level: Set compression level 1-9 (more info later)


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
In my testing, the throughput of the algorithm is somewhere between 20-80MB/s.

If you will not be trnasferring over that speed, you probably should use compression, \
if not, it will only make things slower.

I will do further testing on the subject, and make a matrix, \
but using compression is severely over represented in guides and examples online, \
and most networks can transfer well over 80MB/s and much more when done locally.


## Compression testing
### Parameters
All of this testing was performed between SSDs on this system:
```
                                      pyro@vm-rig
      `-/+++++++++++++++++/-.`        -----------
   `/syyyyyyyyyyyyyyyyyyyyyyys/.      OS: Oracle Linux Server 7.9 x86_64
  :yyyyo/-...............-/oyyyy/     Kernel: 5.4.17-2036.100.6.1.el7uek.x86_64
 /yyys-                     .oyyy+    Uptime: 14 mins
.yyyy`                       `syyy-   Packages: 594 (rpm)
:yyyo                         /yyy/   Shell: bash 4.2.46
.yyyy`                       `syyy-   Theme: Adwaita [GTK3]
 /yyys.                     .oyyyo    Icons: Adwaita [GTK3]
  /yyyyo:-...............-:oyyyy/`    Terminal: /dev/pts/0
   `/syyyyyyyyyyyyyyyyyyyyyyys+.      CPU: Intel i5-3570K (4) @ 3.800GHz
     `.:/+ooooooooooooooo+/:.`        GPU: Intel HD Graphics
                                      Memory: 182MiB / 15417MiB
                                      
[root@vm-rig backup-dev]# rsync --version
rsync  version 3.1.2  protocol version 31
Copyright (C) 1996-2015 by Andrew Tridgell, Wayne Davison, and others.
Web site: http://rsync.samba.org/
Capabilities:
    64-bit files, 64-bit inums, 64-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes, prealloc
```

For the test I used the files from a dev vm I have on the system totalling 29.43G,
it's of a large enough size to deplete any kind of cache and is somewhat compressable.

### Results

| ID | Compression level | Transfer speed | Throughput | Time | Speedup |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| 0 | None | 284.37MB/s | 284.37M MB/s | 1m42s | 1.00 |
| 1 | Default (6) | 16.60MB/s | 34.69MB/s | 14m08s | 2.09 |
| 2 | 1 | 30.75MB/s | 61.19MB/s | 8m00s | 1.99 |
| 3 | 2 | 29.07MB/s | 58.43MB/s | 8m23s | 2.01 |
| 4 | 4 | 24.60MB/s | 48.36MB/s | 9m40s | 2.06 |
| 5 | Max (9) | 5.30MB/s | 10.59MB/s | 44m10s | 2.10 |

### Conclusion

Compression in all forms have heavy penalties and very limited return on compression level, \
I have yet to see any exceptions to this rule with this or any other compression.

So if your uncompressed transfer speed is under 60MB/s, and have CPU power to spare, \
you can save some minutes of transfer speed with compression level 1.

I can see there being some suecases for compression level 1, but not really anything above it.
Another thing to keep in mind is that the CPU used in the example is getting on a bit, \
and the gap between it and the current CPUs on the market will only continue to grow as time passes, \
and the same goes for network speeds and you will have to do your own testing and benchmarking.

The last variable is your data set, I specifically chose a virtual disk due to it being compressable, \
however a lot of data these days comes pre-compressed, so images, video, audio and often ebooks/documents \
may have no benefit from compression what so ever, but will still slow down your transfer.

### Commands and debug data:

| ID | Command | Debug | 
| ----------- | ----------- | ----------- |
| 0 | time rsync -avh --info=progress2 /storage/VM/backup-dev ./ | sent 29.43G bytes <br/> received 1.04K bytes <br/> 284.37M bytes/sec total size is 29.43G <br/> speedup is 1.00 <br/> real    1m42.889s |
| 1 | time rsync -avhz --info=progress2 /storage/VM/backup-dev ./ | sent 14.09G bytes <br/> received 1.04K bytes <br/> 16.60M bytes/sec total size is 29.43G <br/> speedup is 2.09 real  <br/> real  14m8.504s |
| 2 | time rsync -avhz --compress-level=1 --info=progress2 /storage/VM/backup-dev ./ | sent 14.78G bytes  received 1.04K bytes <br/> 30.75M bytes/sec <br/> total size is 29.43G  speedup is 1.99 <br/> real    8m0.107s |
| 3 | time rsync -avhz --compress-level=2 --info=progress2 /storage/VM/backup-dev ./ | sent 14.64G bytes  received 1.04K bytes <br/> 29.07M bytes/sec <br/> total size is 29.43G  speedup is 2.01 <br/> real    8m22.529s |
| 4 | time rsync -avhz --compress-level=4 --info=progress2 /storage/VM/backup-dev ./ | sent 14.30G bytes  received 1.04K bytes <br/> 24.60M bytes/sec <br/> total size is 29.43G  speedup is 2.06 <br/> real    9m40.316s |
| 5 | time rsync -avhz --compress-level=9 --info=progress2 /storage/VM/backup-dev ./ | sent 14.04G bytes  received 1.04K bytes <br/> 5.30M bytes/sec <br/> total size is 29.43G <br/> speedup is 2.10 <br/> real    44m9.844s |
