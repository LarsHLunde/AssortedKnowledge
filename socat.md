# Socat Cookbook
## Adding SSL to HTTP server
```
openssl req -new -newkey rsa:4096 -x509 -sha256 -days 3650 -nodes -out socat.crt -keyout socat.key
socat ssl-l:443,cert=socat.crt,key=socat.key,verify=0,fork,reuseaddr tcp4:127.0.0.1:80
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
UDP (untested):  
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
socat tcp-l:4443,fork,reuseaddr file:'test.html'
```  
