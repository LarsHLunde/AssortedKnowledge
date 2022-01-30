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




[^1]: In a real world scenario you would be making a stricter  
firewall entry to not have anyone unintended access it  
however in this guide, this is something you will have to  
configure later on your own time.  

[^2]: The portal as you can see in the list listens on all ports  
this is bad practice security wise and could be catastrophic in  
a scenario where you want to force it over a specific interface.  



