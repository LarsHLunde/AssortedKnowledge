# How to install a single host AWX k3s cluster on Oracle Linux 9
## Intro
TODO  
based on : https://github.com/kurokobo/awx-on-k3s#awx-on-single-node-k3s
  
## Commands
  
systemctl disable firewalld --now  
dnf install -y git curl  
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION=v1.29.6+k3s2 sh -s - --write-kubeconfig-mode 644
  
cd ~
git clone https://github.com/kurokobo/awx-on-k3s.git
cd awx-on-k3s
git checkout 2.19.1
kubectl apply -k operator
  
Wait for everything to be up:  
watch kubectl -n awx get all  

AWX_HOST="192.168.0.228"
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -out ./base/tls.crt -keyout ./base/tls.key -subj "/CN=${AWX_HOST}/O=${AWX_HOST}" -addext "subjectAltName = DNS:${AWX_HOST}"

vi base/awx.yaml
hostname: 192.168.0.228

sudo mkdir -p /data/postgres-15
sudo mkdir -p /data/projects
sudo chown 1000:0 /data/projects

kubectl apply -k base

kubectl -n awx logs -f deployments/awx-operator-controller-manager

watch kubectl -n awx get awx,all,ingress,secrets


