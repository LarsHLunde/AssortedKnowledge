## Set hostname
```
sudo hostnamectl set-hostname example.com
```

## Purge cloud-init
```
echo 'datasource_list: [ None ]' | sudo -s tee /etc/cloud/cloud.cfg.d/90_dpkg.cfg 
sudo apt-get purge cloud-init -y
sudo rm -rf /etc/cloud/; sudo rm -rf /var/lib/cloud/ 
```

## Open networking
```
sudo iptables -P INPUT ACCEPT 
sudo iptables -P OUTPUT ACCEPT 
sudo iptables -P FORWARD ACCEPT 
sudo iptables -F 
```

## Open networking in /etc/rc.local
```
#!/bin/sh -e
iptables -P INPUT ACCEPT 
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD ACCEPT 
iptables -F 
exit 0
```
  
Megaline of the one above  
```  
echo -e "#\!bin/sh -e \niptables -P INPUT ACCEPT \niptables -P OUTPUT ACCEPT \niptables -P FORWARD ACCEPT \niptables -F \nexit 0" | sudo tee /etc/rc.local && sudo chmod +x /etc/rc.local
```  
  
## Update and reboot
```
sudo apt update 
sudo apt upgrade -y
sudo reboot
```

## Install basics
```
sudo apt install -y vim nano build-essential telnet netcat net-tools iputils-ping policykit-1 lsof dialog apt-utils software-properties-common psmisc systemd-cron curl p7zip-full
```

## Add new user
```  
useradd -m -s /bin/bash pyro
usermod -a -G sudo pyro
passwd pyro
```  

## visudo nopass for user
```  
pyro ALL=(ALL) NOPASSWD: ALL
```

## Full desktop
Please do not do this on an instance with less than 2GB \
and run the install basic above first
```
sudo apt update
sudo apt install -y tigervnc-standalone-server mate-desktop-environment ubuntu-mate-themes firefox
vncserver -geometry 1920x1080
```

## Wireguard
Use the agristan script, then make some alterations to /etc/wireguard/wg0.conf
```
PostUp = iptables -I INPUT 5 -p udp --dport 55555 -j ACCEPT; iptables -I FORWARD 1 -i ens3 -o wg0 -j ACCEPT; iptables -I FORWARD 2 -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE; ip6tables -A FORWARD -i wg0 -j ACCEPT; ip6tables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
PostDown = iptables -D -p udp --dport 55555 -j ACCEPT; iptables -D FORWARD -i ens3 -o wg0 -j ACCEPT; iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o ens3 -j MASQUERADE; ip6tables -D FORWARD -i wg0 -j ACCEPT; ip6tables -t nat -D POSTROUTING -o ens3 -j MASQUERADE
```
