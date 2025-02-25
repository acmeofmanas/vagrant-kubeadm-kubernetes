
# Vagrantfile and Scripts to Automate Kubernetes Setup using Kubeadm [Practice Environemnt for CKA/CKAD and CKS Exams]

## Documentation

Refer this link for documentation: https://devopscube.com/kubernetes-cluster-vagrant/

If you are preparing for CKA, CKAD, CKS or KCNA exam, save $57 using code **SCOFFER15** at https://kube.promo/latest

Current k8s version for CKA, CKAD and CKS exam: 1.22

## Prerequisites

1. Working Vagrant setup
2. Working parallel Desktop
3. OS box is modified for Mac Arm64 users
4. It will provision Master node 1.5GB memory & 1 CPU; 3 worker node with 1gb memory and 1 cpu

## For MAC Users

Latest version of Virtualbox for Mac/Linux can cause issues because you have to create/edit the /etc/vbox/networks.conf file and add:
<pre>* 0.0.0.0/0 ::/0</pre>

So that the host only networks can be in any range, not just 192.168.56.0/21 as described here:
https://discuss.hashicorp.com/t/vagrant-2-2-18-osx-11-6-cannot-create-private-network/30984/23
 
## Usage/Examples

To provision the cluster, execute the following commands.

```shell
git clone https://github.com/scriptcamp/vagrant-kubeadm-kubernetes.git
cd vagrant-kubeadm-kubernetes
vagrant up
```

## Set Kubeconfig file varaible.

```shell
cd vagrant-kubeadm-kubernetes
cd configs
export KUBECONFIG=$(pwd)/config
```

or you can copy the config file to .kube directory.

```shell
cp config ~/.kube/
```

## Kubernetes Dashboard URL

```shell
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=kubernetes-dashboard
```

## Kubernetes login token

Vagrant up will create the admin user token and saves in the configs directory.

```shell
cd vagrant-kubeadm-kubernetes
cd configs
cat token
```

## To shutdown the cluster, 

```shell
vagrant halt
```

## To restart the cluster,

```shell
vagrant up
```

## To destroy the cluster, 

```shell
vagrant destroy -f
```

## Centos & HA based Setup

If you want Centos based setup, please refer https://github.com/marthanda93/VAAS
  
