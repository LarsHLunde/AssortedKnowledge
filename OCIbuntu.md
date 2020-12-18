# Purge cloud-init
echo 'datasource_list: [ None ]' | sudo -s tee /etc/cloud/cloud.cfg.d/90_dpkg.cfg
sudo apt-get purge cloud-init
sudo rm -rf /etc/cloud/; sudo rm -rf /var/lib/cloud/

# Open networking
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F

# Update and reboot
apt update
apt upgrade -y

# Install basics

