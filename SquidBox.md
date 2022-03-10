# Squid secure portal out

## This is currently a stub  
  
## OEL nmcli config
```
sudo nmcli con mod ens33 ipv6.method ignore
nmcli con mod ens33 ipv4.dns "1.1.1.1 8.8.8.8"
reboot
``` 

## UFW config
```
echo -e "y\n" | ufw reset
echo -e "y\n" | ufw delete 1
echo -e "y\n" | ufw delete 1
echo -e "y\n" | ufw delete 1
ufw allow in to any port 22 from 192.168.0.0/24
ufw allow in to any port 3128 from 192.168.0.0/24
ufw allow out from any to any port 443
ufw allow out from any to 1.1.1.1 port 53
ufw allow out from any to 8.8.8.8 port 53
ufw default deny outgoing
echo -e "y\n" | ufw enable
ufw status verbose
```  

## Squid Config
/etc/squid/squid.conf  
```
http_access allow localhost manager
http_access deny manager
acl whitelist dstdomain .redhat.com  wiki.squid-cache.org .debian.org .oracle.com
http_access allow whitelist
http_access deny all
http_port 3128
```  

## Resolve
/etc/resolv.conf  
```
domain home
search home
nameserver 1.1.1.1
nameserver 8.8.8.8
```  
