# How to install samba on a Debian instance
## Pre-reqs
First install samba:  
```
sudo apt install samba
```  
then add a samba password for your user:  
```
sudo smbpasswd -a pyro
```  

## Add a share
First make sure that the share is owned by  
the user you have assigned.  
Then append something like this to  
the file ```/etc/samba/smb.conf```  
```
[storage]
    comment = Storage
    path = /storage
    writeable = yes
    valid users = pyro
    guest ok = yes
```

## Enabling and restarting the service
```
sudo systemctl enable smbd
sudo systemctl restart smbd
```
