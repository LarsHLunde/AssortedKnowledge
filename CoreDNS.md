# Poor Man's DNS
## Intro
The intro is to add context and is not really necessary,  
however, it does tell a real-life story of my adventures as an IT consultant.  
  
It all started with working for a company that shall not be named,  
they were running a spark-based system for moving data between different  
data storage mechanisms, and every time it runs a task, it would build  
a complete Kubernetes cluster from scratch, run a Java batch job,  
then remove the cluster again with keys, adapters, and everything.  
  
The problem was that they put dev and prod on the same network,  
and that they had 2 services (with signed certificates) for 2 different IPs,  
so if they changed the DNS for the dev environment for data.example.com,  
the production machines on the same network would stop being able to resolve,  
and we were setting up a new dev environment.  
  
We thought, maybe the pods would inherit the hosts file from the host,  
this was not the case, so we tried adding them to the pods through  
configurations or manually injecting them into the pods.  
We did not find a good way to do either.  
  
That's when I thought, does it inherit the DNS from the host machine?  
Sure enough, it did, and as such I needed to find an easy way of setting up  
a DNS for this 1 machine that would resolve data.example.com and upstream the rest,  
to the official DNS servers the company is using.  

I would also make the case that you could use this as a normal DNS service for your network,  
test some limitations and look at how I would set it up.

## Setting it up
Note: I will probably create a docker instance just for this purpose,  
so if you would prefer that, I'd see if I'd made it yet.  
  
For now, we are going to be installing it on a Debian VM,  
but it's already been done in the same way on a RHEL 8.9 VM.  
  
All actions are to be done as **root**.  
  
First, create a folder for the CoreDNS installation and cd in to it:  
```
mkdir -p /opt/coredns
cd /opt/coredns
```  
then we need to download and extract the pre-compiled CoreDNS binary:  
```
curl -L -O https://github.com/coredns/coredns/releases/download/v1.11.1/coredns_1.11.1_linux_amd64.tgz
tar -xvf coredns_1.11.1_linux_amd64.tgz
chmod +x coredns
rm -rf coredns_1.11.1_linux_amd64.tgz
```  
Next up is creating a basic config file for CoreDNS, 
for this example, we are establishing the domain "example.com" for local use,  
and we are upstreaming all other requests to 1.1.1.1 and 1.0.0.1.  
Create the file with **nano /opt/coredns/coredns.conf** and add the following:  
```
example.com {
    hosts
}
. {
    forward . 1.1.1.1 1.0.0.1
}
```  
Before we continue, I should go through the config,  
the first block says that if it gets any request for the domain OR any subdomain of example.com,  
it should ONLY check the local systems' /etc/hosts file.  
You can change it to a different hosts file by modifying the hosts line with ```    hosts /opt/coredns/hosts```.  
The second block says that any other requests should be sent to 1.1.1.1 and 1.0.0.1 in a round-robin fashion.  
You are free to set whatever DNS services you want for those addresses. 

Next up is to check if there is already any DNS services running on the system,  
on the RHEL system, which came from Azure's web store,  
there was a systemd dns service running bound to the localhost IP.  
Run the command ```netstat -tulpn | grep 53```,  
if the second number in the third column doesn't say anything for any of the results 
you're in the clear, if it looks something like this:  
```
root@debian-docker:~# netstat -tulpn | grep 53
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      15608/./coredns
udp        0      0 127.0.0.1:53            0.0.0.0:*                           15608/./coredns
```
You will get a port conflict and you must add an IP binding clause to your DNS config.  
This is what it would look like for my local network, but yours might differ:  
```
example.com {
    bind 10.0.0.182
    hosts
}
. {
    bind 10.0.0.182
    forward . 1.1.1.1 1.0.0.1
}
```  
Before starting up we need to add some entries to our hosts file,  
I will just be using the system hosts file at **/etc/hosts**,  and add the following:  
```
1.2.3.4         example.com
2.3.4.5         test1.example.com
3.4.5.6         test2.example.com
```  
then we can start the DNS service:  
```
cd /opt/coredns
./coredns -conf coredns.conf
```  
Open a new terminal, and it's time for testing.  
  
First we run a dig command for example.com without our new DNS,  
and we should be getting no answer, as you can see, there is no answer section:
```
root@debian-docker:~# dig example.com

; <<>> DiG 9.18.24-1-Debian <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 18210
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.                   IN      A

;; Query time: 0 msec
;; SERVER: 10.0.0.1#53(10.0.0.1) (UDP)
;; WHEN: Fri Jul 05 13:45:21 BST 2024
;; MSG SIZE  rcvd: 29
```  
However, if we dig against our IP, we will get the answer from our hosts file:  
``` 
root@debian-docker:~# dig example.com @10.0.0.182

; <<>> DiG 9.18.24-1-Debian <<>> example.com @10.0.0.182
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10007
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: da56955ae0a9064f (echoed)
;; QUESTION SECTION:
;example.com.                   IN      A

;; ANSWER SECTION:
example.com.            3600    IN      A       1.2.3.4

;; Query time: 0 msec
;; SERVER: 10.0.0.182#53(10.0.0.182) (UDP)
;; WHEN: Fri Jul 05 13:46:09 BST 2024
;; MSG SIZE  rcvd: 79
```  
Same goes for our subdomains:  
```
root@debian-docker:~# dig test1.example.com @10.0.0.182

; <<>> DiG 9.18.24-1-Debian <<>> test1.example.com @10.0.0.182
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27364
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: a14e9a88f0d19de3 (echoed)
;; QUESTION SECTION:
;test1.example.com.             IN      A

;; ANSWER SECTION:
test1.example.com.      3600    IN      A       2.3.4.5

;; Query time: 0 msec
;; SERVER: 10.0.0.182#53(10.0.0.182) (UDP)
;; WHEN: Fri Jul 05 13:56:45 BST 2024
;; MSG SIZE  rcvd: 91
```  
Then we test our upstream, and check that it works with google.com:  
```
root@debian-docker:~# dig google.com @10.0.0.182

; <<>> DiG 9.18.24-1-Debian <<>> google.com @10.0.0.182
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56916
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             275     IN      A       216.58.207.206

;; Query time: 35 msec
;; SERVER: 10.0.0.182#53(10.0.0.182) (UDP)
;; WHEN: Fri Jul 05 13:58:16 BST 2024
;; MSG SIZE  rcvd: 65
```  
and finally, according to the documentation, it re-reads the file every 5 seconds:  
https://coredns.io/plugins/hosts/  
So it should be able to do a higher volume of requests, and you can add new entries without restarting the service.  
  
To test, you can add the line: ```4.5.6.7         test3.example.com``` to **/etc/hosts** and do a new dig:  
```
root@debian-docker:~# dig test3.example.com @10.0.0.182

; <<>> DiG 9.18.24-1-Debian <<>> test3.example.com @10.0.0.182
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18924
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: 55f44e3ab27c9f93 (echoed)
;; QUESTION SECTION:
;test3.example.com.             IN      A

;; ANSWER SECTION:
test3.example.com.      3600    IN      A       4.5.6.7

;; Query time: 0 msec
;; SERVER: 10.0.0.182#53(10.0.0.182) (UDP)
;; WHEN: Fri Jul 05 14:02:55 BST 2024
;; MSG SIZE  rcvd: 91
```  

## Creating a service 
This is based on the one from the official Git repo,  
but I think it's more than it needs to be, so I wrote my own.  
  
The official one: https://github.com/coredns/deployment/blob/master/systemd/coredns.service  
  
Open a new systemd service file with: ```nano /etc/systemd/system/coredns.service``` and add the following:  
```
[Unit]
Description=CoreDNS DNS server
Documentation=https://coredns.io
After=network.target

[Service]
Type=simple
Restart=always
WorkingDirectory=/opt/coredns
ExecStart=/opt/coredns/coredns -conf=coredns.conf

[Install]
WantedBy=multi-user.target
```  
Then we reload systemd and activate our new service (make sure the other instance is stopped).  
```
systemctl daemon-reload
systemctl enable coredns --now
systemctl status coredns
```

Now you can propagate your new DNS to your heart's desire,  
and feel free to check out stuff like upgrading all your DNS requests to use TLS  
and other neat features of CoreDNS.
