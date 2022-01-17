# Installing pre-reqs for vmware on different systems

## OEL 8
```
ls -l /boot/vmlinuz*
grubby --set-default /boot/vmlinuz-4.18.0-305.19.1.el8_4.x86_64
reboot
sudo yum install -y oracle-epel-release-el8
sudo yum groupinstall -y "development tools"
sudo yum install -y fonts-tweak-tool libXtst xauth kernel-devel libaio libaio-devel
cd
git clone -b workstation-16.2.1 https://github.com/mkubecek/vmware-host-modules.git
cd vmware-host-modules/
sudo tar -cf vmmon.tar vmmon-only
sudo tar -cf vmnet.tar vmnet-only
sudo cp vmmon.tar vmnet.tar /usr/lib/vmware/modules/source/
cd 
rm -rf vmware-host-modules/
```

## CentOS/fedora/Rocky

```
sudo yum install -y epel-release
sudo yum groupinstall -y "development tools"
sudo yum install -y fonts-tweak-tool libXtst xauth kernel-devel libaio libaio-devel
cd
git clone -b workstation-16.2.1 https://github.com/mkubecek/vmware-host-modules.git
cd vmware-host-modules/
sudo tar -cf vmmon.tar vmmon-only
sudo tar -cf vmnet.tar vmnet-only
sudo cp vmmon.tar vmnet.tar /usr/lib/vmware/modules/source/
cd 
rm -rf vmware-host-modules/
```
