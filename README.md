# database-in-k8s

insatll-node.sh script stolen from:
https://medium.com/faun/kubernetes-prerequisites-for-setup-kubenetes-cluster-part-2-699b3f93d6cc

initial settings:
https://blog.alexellis.io/kubernetes-in-10-minutes/

On master node:
```
sudo kubeadm init --apiserver-advertise-address=<ip of master node>

sudo useradd user -G sudo -m -s /bin/bash
$ sudo passwd user

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
