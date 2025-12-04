# Setting up site2site OpenVPN

## Generate a key
```openvpn --genkey --secret secret.key```  

# UDP version
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
# TCP verison

## Server side
```
dev tun
proto tcp-server          
lport 443
remote <CLIENT IP>
rport 443

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
proto tcp-client
rport 443
remote <SERVER IP>

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

# Both

## Starting tunnel
```
openvpn --config tunnel.cfg
```  

## Adding manual routes
```
ip ro add 10.251.0.0/24 via 10.200.0.1
```

# Systemd service
```  
sudo vi /etc/systemd/system/openvpn-tunnel.service
```  
```  
[Unit]
Description=OpenVPN Tunnel
After=network-online.target
Wants=network-online.target

[Service]
Type=simple
WorkingDirectory=/etc/openvpn
ExecStart=/usr/sbin/openvpn --config /etc/openvpn/tunnel.conf
Restart=always
RestartSec=5
LimitNOFILE=65536

[Install]
WantedBy=multi-user.target
```  
  
Start up:  

```
sudo systemctl daemon-reload
sudo systemctl restart openvpn-tunnel
```  


## Notes
Add individiaul ports for each tunnel.  
Add invidividual log files for each tunnel.  
  
Maybe only do manual routing?  
  
Not use daemon and Supervisord the processes?  
May require that routes are re-added upon crash!  
