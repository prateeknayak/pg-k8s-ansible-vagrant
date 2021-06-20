# Playground repo to build k8s on vagrant with ansible

## Build VMs

- From the root of the repo 
`vagrant up`

*Note:* if you choose to change the ip address that Vagrant is going to use to provision the nodes with then make sure you update ansible inventory as well. This is not automated just yet.

## Ansible play
- From the root of the repo 
`ansible-playbook install-k8s.yaml`

# NOTE: 
This is mostly inspired from other resources which provision k8s using ansible  on vagrant
Official K8s blog: https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/
Kyle Bai: https://github.com/kairen/kubeadm-ansible


