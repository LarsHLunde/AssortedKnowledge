# Setting up site2site OpenVPN

## Generate a key
```openvpn --genkey --secret secret.key```  

## Server side
```
dev tun
proto udp
lport  1194
remote <CLIENT IP>
rport  1194

secret secret.key 0
ifconfig 10.200.0.1 10.200.0.2
route 10.0.0.0 255.255.255.0

persist-tun
persist-key
keepalive 10 60
ping-timer-rem
cipher AES-256-CBC

verb 3
daemon
log-append /tmp/openvpn.log
```  

## Client side
```
dev tun
proto udp
lport  1194
remote <SERVER IP>
rport  1194

secret secret.key 1
ifconfig 10.200.0.2 10.200.0.1
route 10.251.0.0 255.255.255.0

persist-tun
persist-key
keepalive 10 60
ping-timer-rem
cipher AES-256-CBC

verb 3
daemon
log-append /tmp/openvpn.log
```  

## Starting tunnel
```
openvpn --config tunnel.cfg
```  

## Adding manual routes
```
ip ro add 10.251.0.0/24 via 10.200.0.1
```

## Notes
Add individiaul ports for each tunnel.  
Add invidividual log files for each tunnel.  
  
Maybe only do manual routing?  
  
Not use daemon and Supervisord the processes?  
May require that routes are re-added upon crash!  
