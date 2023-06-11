# How to set up VNC Mate Desktop for Oracle Linux 8 servers

## Installing the EPEL repo

First step is to install the EPEL repo from Oracle,  
which will provide us with all the packets we need.  
  
```
sudo dnf install -y oracle-epel-release-el8
```  
## Installing packages and firewall

The second step is installing all the dependencies  
and all the packets MATE needs to operate normally through VNC:  

```
sudo dnf install -y mate-desktop mate-session-manager mate-utils caja marco mate-terminal tigervnc-server
```  
  
as well as some tools I need for the setup I need this for:  
  
```
sudo dnf install -y virt-viewer firefox
```  
  
Finally we open the firewall for VNC:  
```
sudo firewall-cmd --permanent --add-port=5901/tcp
sudo firewall-cmd --reload
```  
  
## Generating and modifying config

The first time you start the VNC server, it will generate the config,  
set passwords and everything else, so we start by running **vncserver**

```
[root@olvm-engine ~]# vncserver

You will require a password to access your desktops.

Password:
Verify:
Would you like to enter a view-only password (y/n)? n
A view-only password is not used

New 'olvm-engine.local:1 (root)' desktop is olvm-engine.local:1

Creating default startup script /root/.vnc/xstartup
Creating default config /root/.vnc/config
Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/olvm-engine.local:1.log

[root@olvm-engine ~]#
```  
You can connect to this instance already, it will however be ugly and barely usable,  
so we need to kill it, and change the xstartup script, in this case **/root/.vnc/xstartup**.  
```
[root@olvm-engine ~]# vncserver -kill :1
Killing Xvnc process ID 8869
[root@olvm-engine ~]#
```  

in the **/root/.vnc/xstartup** file,  comment out the xinitrc line and insert mate session.  
Before:  
```
#!/bin/sh

unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
/etc/X11/xinit/xinitrc
# Assume either Gnome will be started by default when installed
# We want to kill the session automatically in this case when user logs out. In case you modify
# /etc/X11/xinit/Xclients or ~/.Xclients yourself to achieve a different result, then you should
# be responsible to modify below code to avoid that your session will be automatically killed
if [ -e /usr/bin/gnome-session ]; then
    vncserver -kill $DISPLAY
fi
```  
After:  
```
#!/bin/sh

unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
#/etc/X11/xinit/xinitrc
mate-session
# Assume either Gnome will be started by default when installed
# We want to kill the session automatically in this case when user logs out. In case you modify
# /etc/X11/xinit/Xclients or ~/.Xclients yourself to achieve a different result, then you should
# be responsible to modify below code to avoid that your session will be automatically killed
if [ -e /usr/bin/gnome-session ]; then
    vncserver -kill $DISPLAY
fi
```  

You can now manually start the VNC in fully working mode with **vncserver**  
Feel free to edit the geometry with **vncserver -geometry 1920x1080** .

## Setting VNC up as a service
I blatantly stole this from spinxz:  
https://gist.github.com/spinxz/1692ff042a7cfd17583b#file-vncserver-1-service  
  
First kill the existing vnc server with **vncserver -kill :1**  

```
# 1. Copy this file to /etc/systemd/system/vncserver@:1.service
# 2. Edit User=
#    e.g "User=paul"
# 3. Edit the vncserver parameters appropriately in the ExecStart= line!
#    e.g. the -localhost option only allows connections from localhost (or via ssh tunnels)
# 4. Run `systemctl daemon-reload`
# 5. Run `systemctl enable vncserver@:1.service --now`
#

[Unit]
Description=Remote desktop service (VNC)
After=syslog.target network.target

[Service]
Type=forking
User=root

# Clean any existing files in /tmp/.X11-unix environment
ExecStartPre=/bin/sh -c '/usr/bin/vncserver -kill %i > /dev/null 2>&1 || :'
ExecStart=/usr/bin/vncserver -geometry 1900x900
ExecStop=/usr/bin/vncserver -kill %i

[Install]
WantedBy=multi-user.target
```

## Optionally install noVNC
Why use VNC when you could use noVNC!  
noVNC basically turns VNC in to a website using html5 and canvas.  
  
First install noVNC from the repo:  
```
sudo dnf install -y novnc
```    
  
Then generate an some certificates for encryption:  
```
openssl req -new -newkey rsa:4096 -x509 -sha256 -days 3650 -nodes -out /root/novnc.pem -keyout /root/novnc.pem
```  
  
Install a new service for noVNC by putting the following in /etc/systemd/system/novnc.service
```
[Unit]
Description=noVNC service
After=vncserver@:1.service

[Service]
Type=simple
Restart=always
User=root
ExecStart=/usr/bin/websockify --web=/usr/share/novnc/ --cert=/root/novnc.pem 6080 localhost:5901 

[Install]
WantedBy=multi-user.target
```  
and enable/run it:  
```
systemctl daemon-reload
systemctl enable novnc --now
```

noVNC should now be available on port 6080:  
[https://olvm-engine.local:6080/](https://olvm-engine.local:6080/)
