# Installing pre-reqs for vmware on different systems

## OEL 8
```
ls -l /boot/vmlinuz*
grubby --set-default /boot/vmlinuz-4.18.0-305.19.1.el8_4.x86_64
reboot
sudo yum install -y oracle-epel-release-el8
sudo yum groupinstall -y "development tools"
sudo yum install -y fonts-tweak-tool libXtst xauth kernel-devel libaio libaio-devel
https://github.com/mkubecek/vmware-host-modules/tree/workstation-16.1.2
```
