# How to get a VNC connection on your primary screen

Install tigervnc-scraping-server and screen  
```sudo apt-get install screen tigervnc-scraping-server```  

Create a vnc config directory  
```mkdir -p /.vnc```  

Create a vncpasswd file  
```vncpasswd```  

Start the server in a screen  
```screen x0vncserver -passwordfile ~/.vnc/passwd -display :0```

Added to /etc/rc.local
```
#!/bin/sh -e
sleep 3
/usr/sbin/runuser -l pyro -c 'screen -S vnc -fa -d -m x0vncserver -passwordfile ~/.vnc/passwd -display :0'
exit 0
```
