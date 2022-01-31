# How to install an OLVM cluster

## Preparing the KVM hosts
Install your host with Oracle Linux 7, update and reboot.

If your iSCSI is going over a seperate network,  
please add that network as well and check that you get a connection.  

We start with the prequisites:  
```
yum install -y oracle-ovirt-release-el7 net-tools iscsi-initiator-utils
```
Then ```cat /etc/iscsi/initiatorname.iscsi``` to get your iqdn for the iSCSI,  
write it down for later.  

The next step is to configure yum to use the right repos,  
and clean out any old metadata with new metadata from the repos.

```
yum clean all
yum-config-manager --disable ovirt-4.2
yum-config-manager --disable ovirt-4.2-extra
```

Optionally you can open the web managment interface port on 9090
```
firewall-cmd --zone=public --add-port=9090/tcp
sudo firewall-cmd --reload
```  

## Preparing the OLVM host

Install Oracle Linux 7 like normal, , update and reboot. 
Them install some prerequisites:
```
yum install -y oracle-ovirt-release-el7 net-tools ovirt-engine
```

Then we need to disable the old version respository:  
```
yum clean all
yum-config-manager --disable ovirt-4.2
yum-config-manager --disable ovirt-4.2-extra
```  

## Hostname configuration
At this stage we need to set up hostnames in hosts file or DNS,  
in my case I need to append this to all hosts files on local  
computer and all the hosts in the list:  
```
192.168.0.111	   isci.olvm.local
192.168.0.108	   node1.olvm.local
192.168.0.70	   node2.olvm.local
192.168.0.143	   console.olvm.local
```  

## Installing the OLVM
As root, run: ```engine-setup```.  

## Setting up the data center

This part is just an order of operations task.

1. Go to compute -> hosts and add your 2 VM hosts
2. Go to storage -> domains and add your iSCSI/shared storage

Your datacenter should now be up

## Getting the guest tools
The ovirt virtual hardware doesn't play nice with windows,  
and it doesn't come with the gues agent by default, so it needs to be installed.  

Download the iso from the repo with:  
```
yum install -y ovirt-guest-tools-iso
``` 
Download it from the OLVM server, the file is located at ```/usr/share/ovirt-guest-tools-iso```,  
and upload it to the repo like normal, it can now be mounted as a CD to the VM.  


