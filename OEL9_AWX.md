# How to install a single host AWX k3s cluster on Oracle Linux 9
## Intro
TODO  
based on : https://medium.com/@finbarday/deploying-awx-on-single-node-k3s-e951b114d946
  
## Commands
  
systemctl disable firewalld --now  
dnf install -y git curl  
curl -sfL https://get.k3s.io | sh -s - --write-kubeconfig-mode 644  
  
cd ~  
git clone https://github.com/kurokobo/awx-on-k3s.git  
cd awx-on-k3s  
kubectl apply -k operator  
  
Wait for everything to be up:  
watch kubectl -n awx get all  

cd awx-on-k3s
AWX_HOST="192.168.0.158"
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -out ./base/tls.crt -keyout ./base/tls.key -subj "/CN=${AWX_HOST}/O=${AWX_HOST}" -addext "subjectAltName = DNS:${AWX_HOST}"

vi base/awx.yaml
hostname: 192.168.0.158

sudo mkdir -p /data/postgres-15
sudo mkdir -p /data/projects
sudo chmod 755 /data/postgres-15
sudo chown 1000:0 /data/projects

kubectl -n awx logs -f deployments/awx-operator-controller-manager

watch kubectl -n awx get awx,all,ingress,secrets


