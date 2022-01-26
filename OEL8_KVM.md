# OEL KVM machine

## Install virtualization package

```
sudo yum module install -y virt
sudo dnf install -y virt-install virt-viewer
sudo dnf install -y cockpit cockpit-machines
```  
Validate with:  
```
virt-host-validate
```  

## Enable services
```
systemctl enable libvirtd --now
systemctl enable cockpit.socket --now
```  
and validate the services:  
```
systemctl status libvirtd
systemctl status cockpit.socket
```  
  
Add cockpit to firewall if applicable:  
```
firewall-cmd --add-service=cockpit --permanent
firewall-cmd --reload
```  
Cockpit should now be running on port 9090

Remember to make any repos owned by qemu user
