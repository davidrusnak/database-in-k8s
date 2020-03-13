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

mkdir -p $HOME/
sudo cp -i /etc/kubernetes/admin.conf $HOME/config
sudo chown $(id -u):$(id -g) $HOME/config

sudo mkdir -p /var/lib/weave
head -c 16 /dev/urandom | shasum -a 256 | cut -d" " -f1 | sudo tee /var/lib/weave/weave-passwd

kubectl create secret -n kube-system generic weave-passwd --from-file=/var/lib/weave/weave-passwd

kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')&password-secret=weave-passwd&env.IPALLOC_RANGE=192.168.0.0/24"
```

Optional !! Force master to run workload as a slave - only for development when run without other slaves
```
( kubectl taint nodes --all node-role.kubernetes.io/master- )
```


