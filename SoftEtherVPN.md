# SoftEtherVPN
## The server
This guide was made for Ubuntu 16.04, but I am sure it can be adapted to any system.
First install the dependencies:

Ubuntu/Debian : ```sudo apt-get install -y build-essential libmpc-dev flex gcc-multilib```

Then download the latest package for Linux from under http://www.softether-download.com/files/softether/
for example: 

http://www.softether-download.com/files/softether/v4.34-9745-rtm-2020.04.05-tree/Linux/SoftEther_VPN_Server/64bit_-_Intel_x64_or_AMD64/softether-vpnserver-v4.34-9745-rtm-2020.04.05-linux-x64-64bit.tar.gz

untar the package:

```tar xf softether-vpnserver*```

build and deploy
```
cd vpnserver && sudo make
cd .. && sudo mv vpnserver /usr/local && cd /usr/local/vpnserver/
sudo chmod 600 * && sudo chmod 700 vpnserver && sudo chmod 700 vpncmd
```

Time to make a service, this insures that the VPN comes back up after a reboot.
```
sudo vi /lib/systemd/system/vpnserver.service
```
```
[Unit]
Description=SoftEther VPN Server
After=network.target

[Service]
Type=forking
ExecStart=/usr/local/vpnserver/vpnserver start
ExecStop=/usr/local/vpnserver/vpnserver stop

[Install]
WantedBy=multi-user.target
```
Enable, start and start the config tool:
```
sudo systemctl enable vpnserver 
sudo service vpnserver start 
sudo ./vpncmd
```

1. Select 1 for Management of VPN Server
2. Press enter twice to enter admin mode for the server
3. Write **ServerPasswordSet** and set the admin password for the entire server
4. Enter **Hub DEFAULT** to configure the default hub
5. Create a new user with **UserCreate**, you can leave everything but username blank
6. Set the password for your new user with **UserPasswordSet** 
7. Write **SecureNatEnable** to share an internet connection with the VPN user
8. Write **IPsecEnable**
I have some personal preferences here, but you can do whatever you like,
with the exception of the last line. You need to put that as **DEFAULT**
```
Enable L2TP over IPsec Server Function (yes / no): yes
Enable Raw L2TP Server Function (yes / no): no
Enable EtherIP / L2TPv3 over IPsec Server Function (yes / no): yes
Pre Shared Key for IPsec (Recommended: 9 letters at maximum): REDACTED
Default Virtual HUB in a case of omitting the HUB on the Username: DEFAULT
```
Optional: Enable OpenVPN functionality
9. Run **OpenVpnEnable**
```
Enables OpenVPN Clone Server Function (yes / no): yes
UDP Ports to Listen for OpenVPN (Default: 1194 / Multiple Accepted): 1194
```
10. Export the OpenVPN config file with **OpenVpnMakeConfig**
Enter the full path to export to including file name, for example 
```/home/pyro/ovpn.zip```
Said file will be owned by root and have 600 as permission, so you need to fix that.
```
sudo chown pyro ovpn.zip
```
For normal use you want the openvpn_remote_access_l3.ovpn file,
they use their own interal DNS in these files, and you may want to
put your own address in the file instead.
For me it was something like 
```
remote vpn918272870.v4.softether.net 1194
``` 
and you can change it to your personal web address before using it.

## Clients

One of the strongest aspects of the SoftEtherVPN is how trivial it is to connect to them,
I've connected very intuitively to my personal VPN with MacOS, Windows and Android.

In this part I will cover 2 scenarios that are a bit more complex, but equally useful.
Instructions for Windows are towards the bottom.

### Gnome network manager


### Windows

![Windows VPN Config](https://raw.githubusercontent.com/LarsHLunde/AssortedKnowledge/main/resources/vpn-win.png)

![Windows VPN Config2](https://raw.githubusercontent.com/LarsHLunde/AssortedKnowledge/main/resources/vpn-win2.png)

