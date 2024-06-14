# Proxmox Qdevice
## Intro
If you are running a proxmox cluster of only 2 machines, you will not be able to set up HA/failover  
on your virtual machines, because a quorom can not created with just 2 votes.  
  
In this guide I will go through step by step and show you how to set up  
a third vote on a Debian/Ubuntu virtual machine, as it has proven to me to  
be quite the ordeal to set up and it's nice to have a guide for it.  

## Setting up the initial cluster
Just for thoroughness I'll start with 2 fresh proxmox servers,  
and create a cluster from scratch.  

On node 1, go to Datacenter -> Cluster -> Create cluster
  
![image](https://github.com/LarsHLunde/AssortedKnowledge/assets/5747758/d2020063-47e7-4be0-8284-a2851e89ae69)  
Call it something apropriate and save.  

After the cluster is created, under the same menu,  
find the join information button and copy the "join information" it presents:  
  
![image](https://github.com/LarsHLunde/AssortedKnowledge/assets/5747758/3d88d4d7-eb25-47b7-8844-30b5a9ba2378)  
  
On node 2, go to the same menus, but instead of creating a cluster, we are joining one:  
  
![image](https://github.com/LarsHLunde/AssortedKnowledge/assets/5747758/5e4850f9-5ac0-462d-bd0f-d2613b22d833)  

And paste in the join information, the process should take seconds.  
Go back to the first node, and you should see 2 machines in the datacenter:  
  
![image](https://github.com/LarsHLunde/AssortedKnowledge/assets/5747758/5d095914-494f-4716-bf7a-babbfd242615)  
  
## Installing pre-requisites
On the qdevice server and both of the proxmox nodes,
run the following command to add/create support for the qdevice: 
``` 
apt update
apt install -y corosync-qnetd corosync-qdevice
```
The proxmox server will complain while running apt update, you can ignore it.  

## Adding SSH keys for all hosts
This may be puzzling to think about, but if you haven't pre-approved the SSH keys  
for all hosts, on all hosts, the scripts for setting up the qdevice will fail.  
So you will need to run:  
```
ssh-keyscan qdevice-ip-goes-here  >> ~/.ssh/known_hosts
ssh-keyscan node1-ip-goes-here  >> ~/.ssh/known_hosts
ssh-keyscan node2-ip-goes-here  >> ~/.ssh/known_hosts
```
On the qdevice node, node1 and node2 as root.

## Adding pubkeys from the proxmox nodes to the qdevice authorized_keys
There are 2 ways to go about this, the first one is to enable root login over SSH for the qdevice host  
and then proxmox will install it's own private key on the host after you've typed the root password.  

The other way is to go in to the proxmox shell, copy out the contents of ~/.ssh/id_rsa.pub on each node,  
and paste them in to the ~/.ssh/authorized_keys file of the root user for the qdevice host.  

## Adding the qdevice to the cluster
From node 1, open the shell and type in:  
```pvecm status```  
If you look at the last paragraph, it should say:  
```
Membership information
----------------------
    Nodeid      Votes Name
0x00000001          1 192.168.111.110 (local)
0x00000002          1 192.168.111.111
```
That you have 2 nodes with 1 quorom vote each, which is correct.
So now we add a new qdevice with:  
```
pvecm qdevice setup <QDEVICE-IP>
```  
After it's done, run the ```pvecm status``` command, and you should have 3 members with 1 vote each.  
```
Membership information
----------------------
    Nodeid      Votes    Qdevice Name
0x00000001          1    A,V,NMW 192.168.111.110 (local)
0x00000002          1    A,V,NMW 192.168.111.111 
0x00000000          1            Qdevice
```  
You can now set up high availability on your VMs  
  
If the qdevice shows up with no votes:  
```
Membership information
----------------------
    Nodeid      Votes    Qdevice Name
0x00000001          1   A,NV,NMW 192.168.111.110 (local)
0x00000002          1   A,NV,NMW 192.168.111.111
0x00000000          0            Qdevice (votes 1)
```  
The HA will not work, and you need to remove the qdevice from the cluster:
On one of the proxmox nodes: ```pvecm qdevice remove```  
uninstall, reset the configs, delete certificates and reinstall on the qdevice node:  
```
apt remove -y --purge corosync-qdevice corosync-qnetd corosync
rm -rf /etc/corosync/qdevice/net/nssdb
apt install -y corosync-qdevice corosync-qnetd corosync
```  
and re-add to the cluster with force on a proxmox node:  
```
pvecm qdevice setup <QDEVICE-IP> -f
``` 
and it should look like this with ```pvecm status``` command on a proxmox node:  
```
Membership information
----------------------
    Nodeid      Votes    Qdevice Name
0x00000001          1    A,V,NMW 192.168.111.110 (local)
0x00000002          1    A,V,NMW 192.168.111.111 
0x00000000          1            Qdevice
```  
