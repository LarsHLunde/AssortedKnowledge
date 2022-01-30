# How to set up iSCSI

This is a guide on how to set up an iSCSI server and clients,  
or in the iSCSI lingo an iSCSI target and initiators,  
and to connect them all and make them work for you.  

In the guide I will be using Rocky Linux 8 for the target  
and Oracle Linux 7 for the initiators, but it should work  
on any modern linux distribution.  
  
All operations presune you run them as **root**

## Setting up the target

### Prequisites
First we need to install the software with:  
```
yum install -y targetcli
```  
and opening the port for iSCSI [^1] :  
```
firewall-cmd --add-port 3260/tcp --permanent
firewall-cmd --reload
```  

You will also need a mountpoint for the hard-drive,  
RAID, Virtual Drive or what have you for the iSCSI.  
In this example I will be sharing my ```/dev/vdb```.  

Last but not least we need to enable the service:  
```
systemctl enable target --now
```  

### Setttng up the target

The first task on the agenda is to link your drive  
in to the iSCSI target list, so in your terminal write:
```targetcli``` and in the new prompt write ```ls```.  

What you are looking at is the full inventory of the iSCSI manager,  
if you ever have to troubleshoot this is where it happens:

```
[root@localhost ~]# targetcli
targetcli shell version 2.1.53
Copyright 2011-2013 by Datera, Inc and others.
For help on commands, type 'help'.

/> ls
o- / ..................................................................... [...]
  o- backstores .......................................................... [...]
  | o- block .............................................. [Storage Objects: 0]
  | o- fileio ............................................. [Storage Objects: 0]
  | o- pscsi .............................................. [Storage Objects: 0]
  | o- ramdisk ............................................ [Storage Objects: 0]
  o- iscsi ........................................................ [Targets: 0]
  o- loopback ..................................................... [Targets: 0]
/>

```  
When doing a drive over iSCSI, it will be treated as a raw disk,  
this is so that whoever owns the drive have full autonomy  
and leads to less problems down the line.

#### Adding the drive to the inventory 

Time to add ```/dev/vdb``` under the ```/backstores/block```.  
in the targetcli, write ```cd /backstores/block```  
and add the disk as LUN_0 with ```create name=LUN_0 dev=/dev/vdb```.
If we ```cd /``` to the top again and write ```ls```, we can see all went to plan:  
```
[root@localhost ~]# targetcli
targetcli shell version 2.1.53
Copyright 2011-2013 by Datera, Inc and others.
For help on commands, type 'help'.

/> ls
o- / ..................................................................... [...]
  o- backstores .......................................................... [...]
  | o- block .............................................. [Storage Objects: 0]
  | o- fileio ............................................. [Storage Objects: 0]
  | o- pscsi .............................................. [Storage Objects: 0]
  | o- ramdisk ............................................ [Storage Objects: 0]
  o- iscsi ........................................................ [Targets: 0]
  o- loopback ..................................................... [Targets: 0]
/> cd backstores/block
/backstores/block> create name=LUN_0 dev=/dev/vdb
Created block storage object LUN_0 using /dev/vdb.
/backstores/block> cd /
/> ls
o- / ..................................................................... [...]
  o- backstores .......................................................... [...]
  | o- block .............................................. [Storage Objects: 1]
  | | o- LUN_0 .................... [/dev/vdb (750.0GiB) write-thru deactivated]
  | |   o- alua ............................................... [ALUA Groups: 1]
  | |     o- default_tg_pt_gp ................... [ALUA state: Active/optimized]
  | o- fileio ............................................. [Storage Objects: 0]
  | o- pscsi .............................................. [Storage Objects: 0]
  | o- ramdisk ............................................ [Storage Objects: 0]
  o- iscsi ........................................................ [Targets: 0]
  o- loopback ..................................................... [Targets: 0]
/>
```  

#### Set up the target itself  

Next up is setting up the target itself, in ```targetcli``` and ```cd /iscsi```  
write ```create``` and your first target is created, congratulations!  
If we ```cd /``` back to top directory we can see it in the list with iqn and everything.  

```
[root@localhost ~]# targetcli
targetcli shell version 2.1.53
Copyright 2011-2013 by Datera, Inc and others.
For help on commands, type 'help'.

/> ls
o- / ..................................................................... [...]
  o- backstores .......................................................... [...]
  | o- block .............................................. [Storage Objects: 1]
  | | o- LUN_0 .................... [/dev/vdb (750.0GiB) write-thru deactivated]
  | |   o- alua ............................................... [ALUA Groups: 1]
  | |     o- default_tg_pt_gp ................... [ALUA state: Active/optimized]
  | o- fileio ............................................. [Storage Objects: 0]
  | o- pscsi .............................................. [Storage Objects: 0]
  | o- ramdisk ............................................ [Storage Objects: 0]
  o- iscsi ........................................................ [Targets: 0]
  o- loopback ..................................................... [Targets: 0]
/> cd /iscsi
/iscsi> create
Created target iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3.
Created TPG 1.
Global pref auto_add_default_portal=true
Created default portal listening on all IPs (0.0.0.0), port 3260.
/iscsi> cd /
/> ls
o- / ..................................................................... [...]
  o- backstores .......................................................... [...]
  | o- block .............................................. [Storage Objects: 1]
  | | o- LUN_0 .................... [/dev/vdb (750.0GiB) write-thru deactivated]
  | |   o- alua ............................................... [ALUA Groups: 1]
  | |     o- default_tg_pt_gp ................... [ALUA state: Active/optimized]
  | o- fileio ............................................. [Storage Objects: 0]
  | o- pscsi .............................................. [Storage Objects: 0]
  | o- ramdisk ............................................ [Storage Objects: 0]
  o- iscsi ........................................................ [Targets: 1]
  | o- iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 ... [TPGs: 1]
  |   o- tpg1 ........................................... [no-gen-acls, no-auth]
  |     o- acls ...................................................... [ACLs: 0]
  |     o- luns ...................................................... [LUNs: 0]
  |     o- portals ................................................ [Portals: 1]
  |       o- 0.0.0.0:3260 ................................................. [OK]
  o- loopback ..................................................... [Targets: 0]
/>
```

Next, due to wanting to run the iSCSI over a protected interconnect,
I will be changing the portal to only respond on that IP [^2] :  

```
[root@localhost ~]# targetcli
targetcli shell version 2.1.53
Copyright 2011-2013 by Datera, Inc and others.
For help on commands, type 'help'.

/> cd /iscsi/iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3/tpg1/portals/
/iscsi/iqn.20.../tpg1/portals> delete 0.0.0.0 ip_port=3260
Deleted network portal 0.0.0.0:3260
/iscsi/iqn.20.../tpg1/portals> create 192.168.122.2 ip_port=3260
Using default IP port 3260
Created network portal 192.168.122.2:3260.
/iscsi/iqn.20.../tpg1/portals> cd /
/> ls
o- / ..................................................................... [...]
  o- backstores .......................................................... [...]
  | o- block .............................................. [Storage Objects: 1]
  | | o- LUN_0 .................... [/dev/vdb (750.0GiB) write-thru deactivated]
  | |   o- alua ............................................... [ALUA Groups: 1]
  | |     o- default_tg_pt_gp ................... [ALUA state: Active/optimized]
  | o- fileio ............................................. [Storage Objects: 0]
  | o- pscsi .............................................. [Storage Objects: 0]
  | o- ramdisk ............................................ [Storage Objects: 0]
  o- iscsi ........................................................ [Targets: 1]
  | o- iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 ... [TPGs: 1]
  |   o- tpg1 ........................................... [no-gen-acls, no-auth]
  |     o- acls ...................................................... [ACLs: 0]
  |     o- luns ...................................................... [LUNs: 0]
  |     o- portals ................................................ [Portals: 1]
  |       o- 192.168.122.2:3260 ........................................... [OK]
  o- loopback ..................................................... [Targets: 0]
/>
```  

The long string starting with iqn, in our case ```iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3```  
is our target address, keep it in mind for the rest of the guide as you will need to
replace it in the scriipts presented yourself.  

#### Linking in the storage

cd in to your new iSCSI target and go to tpg1 and luns,  
then we add the ```LUN_0``` we defined earlier.  

```
[root@localhost ~]# targetcli
targetcli shell version 2.1.53
Copyright 2011-2013 by Datera, Inc and others.
For help on commands, type 'help'.

/> cd /iscsi/iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3/tpg1/luns/
/iscsi/iqn.20...3a3/tpg1/luns> create /backstores/block/LUN_0
Created LUN 0.
/iscsi/iqn.20...3a3/tpg1/luns> cd /
/> ls
o- / ......................................................................... [...]
  o- backstores .............................................................. [...]
  | o- block .................................................. [Storage Objects: 1]
  | | o- LUN_0 .......................... [/dev/vdb (750.0GiB) write-thru activated]
  | |   o- alua ................................................... [ALUA Groups: 1]
  | |     o- default_tg_pt_gp ....................... [ALUA state: Active/optimized]
  | o- fileio ................................................. [Storage Objects: 0]
  | o- pscsi .................................................. [Storage Objects: 0]
  | o- ramdisk ................................................ [Storage Objects: 0]
  o- iscsi ............................................................ [Targets: 1]
  | o- iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 ....... [TPGs: 1]
  |   o- tpg1 ............................................... [no-gen-acls, no-auth]
  |     o- acls .......................................................... [ACLs: 0]
  |     o- luns .......................................................... [LUNs: 1]
  |     | o- lun0 ...................... [block/LUN_0 (/dev/vdb) (default_tg_pt_gp)]
  |     o- portals .................................................... [Portals: 1]
  |       o- 192.168.122.2:3260 ............................................... [OK]
  o- loopback ......................................................... [Targets: 0]
/>
```  
The iSCSI protocol, at least in this example works on an access list system,  
so we will not be able to test it properly until we get some initiators that can connect.  

## Setting up an initiator
Setting up an initiator is far easier, but is a topic worth covering as well.

I've searched high and low for a better way to do this, but I came up short.  

First we need to install the prerequisites:
``` 
yum install -y iscsi-initiator-utils
```  
and enable the services that got generated:  
```
systemctl enable iscsid --now
systemctl enable iscsiuio --now
```  

Next we need to chekc if we can connect and talk to the target:  
```
iscsiadm -m discovery -t sendtargets -p 192.168.122.2
```  
You should get something like this back:  
```
[root@localhost ~]# iscsiadm -m discovery -t sendtargets -p 192.168.122.2
192.168.122.2:3260,1 iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3
[root@localhost ~]#
```  

If not please review the troubleshooting section on the bottom of the article.  

All initiators have an intiator name that needs to be whitelisted in the target.  

To find yours, run ```cat /etc/iscsi/initiatorname.iscsi``` :  
```
[root@localhost ~]# cat /etc/iscsi/initiatorname.iscsi
InitiatorName=iqn.1988-12.com.oracle:d83691dc4b2
[root@localhost ~]#
```  
And write it down for the next part.

## Connecting the target and initiator
In the fist section of the guide, you may have noticed there was a section named ACLs  
this stands for Access Control Lists, which is the way we whitelist a computer  
to use the iSCSI share. This can be combined with CHAP, a user/pass system,  
but that is outside the scope of this article, we will just use subnets and ACLs.  

On the target machine open ```tagetcli``` again, and ```cd``` your way down  
to the iscsi ACL list (it supports tab completion), then we create the iqn of our new initiator.  
```
[root@localhost ~]# targetcli
targetcli shell version 2.1.53
Copyright 2011-2013 by Datera, Inc and others.
For help on commands, type 'help'.

/> cd /iscsi/iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3/tpg1/acls
/iscsi/iqn.20...3a3/tpg1/acls> create iqn.1988-12.com.oracle:d83691dc4b2
Created Node ACL for iqn.1988-12.com.oracle:d83691dc4b2
Created mapped LUN 0.
/iscsi/iqn.20...3a3/tpg1/acls>
```  

Next, on the initiator side, we now need to attach the iSCSI,  
I recommend you run a ```lsblk``` before and after to see it appear.
First we need to add the target to our discovery database,  
and only then can we mount it [^3] :  
```
iscsiadm -m discovery -t sendtargets -p 192.168.122.2
iscsiadm -m node -T iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 -p 192.168.122.2:3260 -l
```  
```
[root@localhost ~]# lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sr0          11:0    1 1024M  0 rom
vda         251:0    0   30G  0 disk
├─vda2      251:2    0   29G  0 part
│ ├─ol-swap 252:1    0    4G  0 lvm  [SWAP]
│ └─ol-root 252:0    0   25G  0 lvm  /
└─vda1      251:1    0    1G  0 part /boot
[root@localhost ~]# iscsiadm -m discovery -t sendtargets -p 192.168.122.2
192.168.122.2:3260,1 iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3
[root@localhost ~]# iscsiadm -m node -T iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 -p 192.168.122.2:3260 -l
Logging in to [iface: default, target: iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3, portal: 192.168.122.2,3260] (multiple)
Login to [iface: default, target: iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3, portal: 192.168.122.2,3260] successful.
[root@localhost ~]# lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sr0          11:0    1 1024M  0 rom
sda           8:0    0  750G  0 disk
vda         251:0    0   30G  0 disk
├─vda2      251:2    0   29G  0 part
│ ├─ol-swap 252:1    0    4G  0 lvm  [SWAP]
│ └─ol-root 252:0    0   25G  0 lvm  /
└─vda1      251:1    0    1G  0 part /boot
[root@localhost ~]#
```  
and suddenly, a new 750GB disk has appeared, it will persist through reboot as well.

If you fat-fingered something and you're getting random annoying errors,
this is the short guide to removing a target completely:  
```
iscsiadm -m node -T iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 -p 192.168.122.2:3260 -u
iscsiadm -m node -o delete -T 192.168.122.2:3260
iscsiadm -m discoverydb -t sendtargets -p 192.168.122.2:3260 -o delete
```  
The first line kills your session to the iSCSI share,
the second removes it from your node list, it doesn't always show up on there,
and the third removes it from your discovery database, leaving you with a clean slate.

## Troubleshooting
### Setup configuration
You may have missed something in this long guide,  
and your setup might differ from mine, however if a sub-section  
of your ls command is missing or the righ column on mine says 1,  
and yours says 0, I would go back through the guide to see  
if something was missed (run ```cd /``` if you get lost):

```
[root@localhost ~]# targetcli
targetcli shell version 2.1.53
Copyright 2011-2013 by Datera, Inc and others.
For help on commands, type 'help'.

/> ls
o- / ......................................................................... [...]
  o- backstores .............................................................. [...]
  | o- block .................................................. [Storage Objects: 1]
  | | o- LUN_0 .......................... [/dev/vdb (750.0GiB) write-thru activated]
  | |   o- alua ................................................... [ALUA Groups: 1]
  | |     o- default_tg_pt_gp ....................... [ALUA state: Active/optimized]
  | o- fileio ................................................. [Storage Objects: 0]
  | o- pscsi .................................................. [Storage Objects: 0]
  | o- ramdisk ................................................ [Storage Objects: 0]
  o- iscsi ............................................................ [Targets: 1]
  | o- iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 ....... [TPGs: 1]
  |   o- tpg1 ............................................... [no-gen-acls, no-auth]
  |     o- acls .......................................................... [ACLs: 1]
  |     | o- iqn.1988-12.com.oracle:d83691dc4b2 ................... [Mapped LUNs: 1]
  |     |   o- mapped_lun0 ................................. [lun0 block/LUN_0 (rw)]
  |     o- luns .......................................................... [LUNs: 1]
  |     | o- lun0 ...................... [block/LUN_0 (/dev/vdb) (default_tg_pt_gp)]
  |     o- portals .................................................... [Portals: 1]
  |       o- 192.168.122.2:3260 ............................................... [OK]
  o- loopback ......................................................... [Targets: 0]
/>
```

### Service crashed or not enabled

In order for this to work you need the target service to be up on the target,
iscsid and iscsiuio on the initiator:  
```
[root@localhost ~]# service target status
Redirecting to /bin/systemctl status target.service
● target.service - Restore LIO kernel target configuration
   Loaded: loaded (/usr/lib/systemd/system/target.service; enabled; vendor preset: disabled)
   Active: active (exited) since Sun 2022-01-30 05:43:00 EST; 2h 15min ago
 Main PID: 19793 (code=exited, status=0/SUCCESS)
    Tasks: 0 (limit: 9204)
   Memory: 0B
   CGroup: /system.slice/target.service

Jan 30 05:43:00 localhost.localdomain systemd[1]: Starting Restore LIO kernel target configurati>
Jan 30 05:43:00 localhost.localdomain target[19793]: Storage Object block/LUN_0: Cannot set attr>
Jan 30 05:43:00 localhost.localdomain target[19793]: Storage Object block/LUN_0: Cannot set attr>
Jan 30 05:43:00 localhost.localdomain systemd[1]: Started Restore LIO kernel target configuratio>
[root@localhost ~]#
```  
The key lines here are:  
```
Loaded: loaded (/usr/lib/systemd/system/target.service; enabled; vendor preset: disabled)
Active: active (exited) since Sun 2022-01-30 05:43:00 EST; 2h 15min ago
```  
With the words ```Loaded: loaded --- enabled``` and ```Active: active``` being the most important.  

### Firewalls

There could be a thousand different network problems involved,  
but by far the most common is the local firewall.  

On redhat-like systems like in this guide the best option 
is to disable the firewalld service.
```
systemctl disable firewalld --now
```  

In debian based systems your best bet is killing ufw:  
```
systemctl disable ufw --now
```  

If those don't yield any results, you can try to open the iptables completely:  
```
iptables -P INPUT ACCEPT 
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD ACCEPT 
iptables -F 
```

That being said, if this makes your configuration work,  
you should try to find a way to open port 3260 in your firewall instead.  


[^1]: In a real world scenario you would be making a stricter  
firewall entry to not have anyone unintended access it  
however in this guide, this is something you will have to  
configure later on your own time.  

[^2]: The portal as you can see in the list listens on all ports  
this is bad practice security wise and could be catastrophic in  
a scenario where you want to force it over a specific interface.  

[^3]: The full version of that command is:  
iscsiadm --mode node --targetname iqn.2003-01.org.linux-iscsi.localhost.x8664:sn.f5f241f2c3a3 --portal 192.168.122.2 --login  
the shorthand can get confusing sometimes in these linux programs.  
