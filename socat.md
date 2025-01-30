# Socat Cookbook
## Socat systemd service
Add to a service file like ```/etc/systemd/system/socat.service```  
```
[Unit]
Description=Socat Service
Wants=network-online.target
After=network-online.target

[Service]
Type=simple
WorkingDirectory=/root/tls
ExecStart=/usr/bin/socat ssl-l:443,cert=socat.crt,key=socat.key,verify=0,fork,reuseaddr tcp4:127.0.0.1:80
Restart=always

[Install]
WantedBy=multi-user.target
```  
Then refresh systemd and activate:  
``` 
systemctl daemon-reload
systemctl enable socat --now
systemctl status socat
```   
## Socat supervisor service
```
[program:socat-http-to-https-443]
command = socat ssl-l:443,cert=socat.crt,key=socat.key,verify=0,fork,reuseaddr tcp4:127.0.0.1:80
directory=/root/.certs
autorestart = true
user = root
```
## Adding SSL to HTTP server
```
openssl req -new -newkey rsa:4096 -x509 -sha256 -days 3650 -nodes -out socat.crt -keyout socat.key
socat ssl-l:443,cert=socat.crt,key=socat.key,verify=0,fork,reuseaddr tcp4:127.0.0.1:80
```  

## Removing SSL from HTTPS server
Signed Cert:  
```  
socat tcp-l:8080,fork,reuseaddr ssl:google.com:443
```  
Self Signed Cert  
```  
socat tcp-l:8080,fork,reuseaddr ssl:google.com:443,verify=0
```  
## Basic transparent proxies
Normal:  
```
socat tcp-l:2222,reuseaddr,fork tcp:172.22.2.60:22
```  
With bind address:  
```
socat tcp-l:2222,reuseaddr,fork,bind=10.213.3.2 tcp:172.22.2.60:22
```
UDP :  
```
socat udp-l:55555,reuseaddr,fork udp:172.22.2.60:55555
``` 
## Static messages
From command line:  
```
socat tcp-l:80,fork,reuseaddr exec:'echo "Hello world\n"'
```  
From file:  
```
socat tcp-l:4443,fork,reuseaddr exec:'cat test.html'
```  
Basic webpage:  
test.html: 
```
HTTP/1.0 200
ContentType: text/html

<!DOCTYPE html>
<html>
    <head>
        <title>Example</title>
    </head>
    <body>
        <p>This is an example of a simple HTML page with one paragraph.</p>
    </body>
</html>
```  
```
socat tcp-l:4443,fork,reuseaddr exec:'cat test.html'
```
Serving a binary file:  
headers.txt:  
```
HTTP/1.0 200
ContentType: application/octet-stream
Content-Disposition: inline; filename="file.zip"
```  
```
socat tcp-l:4443,fork,reuseaddr exec:'cat headers.txt file.zip'
```  
