

## What's the kind?

`kind` also known as `kubernetes in docker`, it means run `k8s` in docker container, each `k8s` node would be a docker container. so it's super simple compared with `kubeadm` or even `minikube` to setup a `k8s` cluster with `kind`, but it's only suitable for test and learn purpose.

## Deployment procedure 

- the most simple way for the basic cluster.
only one master node with one command-line 

```shell
kind create cluster --name <cluster-name>
```
- you can create a config file for `kind` to create a customized `k8s` cluster.

```shell
kind create cluster --config xxx.yaml -n <cluster-name>
```


###  Setup flannel cni plugin with kind
`Kind` uses [kindnetd](https://github.com/kubernetes-sigs/kind/tree/main/images/kindnetd) based around standard CNI plugins (ptp,  host-local, …) and simple netlink routes as the default networking implementation in default, we can disable it in practice and setup `flannel` cni plugin instead.

Please check the reference below for the details.
## Reference


- https://routemyip.com/posts/k8s/setup/flannel/ 