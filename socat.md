# Socat Cookbook
## Adding SSL to HTTP server
```
openssl req -new -newkey rsa:4096 -x509 -sha256 -days 3650 -nodes -out socat.crt -keyout socat.key
socat ssl-l:443,cert=socat.crt,key=socat.key,verify=0,fork,reuseaddr tcp4:127.0.0.1:80
```  
