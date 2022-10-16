#IPtables library

## Emulate no secure environment
```  
iptables -F
iptables -I INPUT -s 192.168.111.0/24 -j ACCEPT
iptables -I OUTPUT -d  192.168.111.0/24 -j ACCEPT
iptables -I FORWARD -s 192.168.111.0/24 -d 192.168.111.0/24 -j ACCEPT
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
```  
