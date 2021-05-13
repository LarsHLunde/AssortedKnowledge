# Install Syncplay server on Debian 10

**WARNING : Your milage may vary with other Debian based systems**

## User guide
Once you have installed the software you run the command:
```
syncplay-server
```
Do a ctrl-c to stop the server again.  
You will get a randomly generated salt,  
which I encourage you keep and reuse.

Then what I like to do is to create a shell file,
where the salt and password is stored, 
and start the server in a screen, 
so it doesn't close if you lose the SSH session.

```
touch syncplay.sh
chmod +x syncplay.sh
echo "screen -S syncplay syncplay-server --salt REDACTED --password MyPasswordHere" > syncplay.sh
```

To start the server just
```
./syncplay.sh
```

To detach the screen press Ctrl+a+d

You can reattach the screen with
```
screen -r syncplay
```

## Update and reboot
This guide uses sudo, and Debian doesn't always come with sudo  
so we'll start by installing sudo if it's not installed  
updating and upgrading the system to latest version

```
apt-get update
apt-get install -y sudo
apt-get -y upgrade
reboot
```

Monster line version:
```
apt-get update && apt-get install -y sudo && apt-get -y upgrade && reboot
```

## Install script
```
sudo apt-get install -y build-essential curl vim python3-pip python3-twisted cmake libqt4-dev screen
sudo pip3 install PySide2
curl -sL https://github.com/Syncplay/syncplay/archive/refs/tags/v1.6.7.tar.gz | tar xz
cd syncplay-1.6.7/
sudo make install
cd ..
rm -rf syncplay-1.6.7/
```

Monster line version:
```
sudo apt-get install -y build-essential curl vim python3-pip python3-twisted cmake libqt4-dev screen && sudo pip3 install PySide2 && curl -sL https://github.com/Syncplay/syncplay/archive/refs/tags/v1.6.7.tar.gz | tar xz && cd syncplay-1.6.7/ && sudo make install && cd .. && rm -rf syncplay-1.6.7/
```
