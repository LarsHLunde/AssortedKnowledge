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

### CLI only

Download the apropriate client package from http://www.softether-download.com/files/softether/
For example: 
http://www.softether-download.com/files/softether/v4.34-9745-rtm-2020.04.05-tree/Linux/SoftEther_VPN_Client/64bit_-_Intel_x64_or_AMD64/softether-vpnclient-v4.34-9745-rtm-2020.04.05-linux-x64-64bit.tar.gz

untar the package:

```tar xf softether-vpnclient-*```

build and deploy
```
cd vpnclient && sudo make
cd .. && sudo mv vpnclient /usr/local && cd /usr/local/vpnclient/
sudo chmod 600 * && sudo chmod 700 vpnclient && sudo chmod 700 vpncmd
```

Time to start the client and configure the connection

```
sudo ./vpnclient start
sudo ./vpncmd
```
1. Enter **2** for the VPN client, press enter
2. First we need to make a virtual NIC to use with **NicCreate**, we'll call it virt0
3. Create an account with **AccountCreate**
```
Name of VPN Connection Setting: local
Destination VPN Server Host Name and Port Number: 192.168.0.132:443
Destination Virtual Hub Name: DEFAULT
Connecting User Name: pyro
Used Virtual Network Adapter Name: virt0
```
Use your own selected setting name, hostname/ip and username,
but copy the port, hub name and adapter (unless you set it up differently).
4. The password for the account is set seperatley with **AccountPasswordSet** \
when asking for standard or radius, just enter standard, time to test if you can connect.
5. Time to test if you can connect: **AccountConnect**
6. Check if you are connected (can take some seconds) with **AccountList** \
if it says connected, you are connected.
```
VPN Client>AccountList
AccountList command - Get List of VPN Connection Settings
Item                        |Value
----------------------------+--------------------------------------------
VPN Connection Setting Name |local
Status                      |Connected
VPN Server Hostname         |192.168.0.132:443 (Direct TCP/IP Connection)
Virtual Hub                 |DEFAULT
Virtual Network Adapter Name|virt0
The command completed successfully.
```
7. Optional
Set the vpnclient to autoconnect when you start the vpnclient.
Mind you, the vpnclient does not currently autostart on boot.
Use the command **AccountStartupSet** to start a vpn connection when you start the server.
Unlike what you are most likely used to, the computer will **NOT** automatically
route all your data through your new connection, or even give it an IP.
8. Configure dhcp for you new interface:
```
sudo dhclient vpn_virt0
```
9. Add route to vpn for all traffic
```
sudo ip route add 192.168.0.132/32 via 192.168.0.1 dev eth0
```

TODO:
```
/usr/local/vpnclient/vpnclient start && dhclient vpn_virt0 && ip route add 192.168.0.132/32 via 192.168.0.1 dev ens33
dhclient -r vpn_virt0 && /usr/local/vpnclient/vpnclient stop && ip route del 192.168.0.132 via 192.168.0.1 dev ens33 && ifdown ens33 && ifup ens33
```

Service!

### Gnome network manager
To install required packages:

```
sudo apt install network-manager-l2tp-gnome
```

You may need to log in and back out for the button to appear.

Configure a new VPN :

![Gnome VPN Config0](https://raw.githubusercontent.com/LarsHLunde/AssortedKnowledge/main/resources/vpn-gnome0.png)

and write the VPN address, username and password in to the form.

![Gnome VPN Config1](https://raw.githubusercontent.com/LarsHLunde/AssortedKnowledge/main/resources/vpn-gnome1.png)

Then for the tricky part, click IPsec settings marked in red.

![Gnome VPN Config2](https://raw.githubusercontent.com/LarsHLunde/AssortedKnowledge/main/resources/vpn-gnome2.png)

Write pre-shared key you wrote previously in to the apropriate field,
and enter 
```
aes128-sha1-modp2048!
```
In to both Phase algorithms, it will not work without it.

### Windows

![Windows VPN Config](https://raw.githubusercontent.com/LarsHLunde/AssortedKnowledge/main/resources/vpn-win.png)

![Windows VPN Config2](https://raw.githubusercontent.com/LarsHLunde/AssortedKnowledge/main/resources/vpn-win2.png)

