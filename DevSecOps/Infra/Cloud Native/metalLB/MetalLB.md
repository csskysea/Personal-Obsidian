
#devops #devsecops #cloudnatives

## MetalLB 是什么？

`MetalLB` 是一种面向云原生的负载均衡器，我们知道在云厂商平台上构建的`k8s` 集群通常会提供云负载均衡器如阿里云的`SLB`, aws 的`ELB`, 作为外部客户端访问`k8s` 集群内部服务的入口，一般会有一个public ip , 然后云管理员可以在这个负载均衡器下绑定一个或多个work node 上的port,这个port 也就是提前部署在`K8S` 集群上的ingress controller service 的port（网络协议可以是http + port也有可能是TCP+port ），通过这样的方式将外部访问流量引到集群内部。流量路径为：
slb -> ingress controller-> service-> endpoints。

但是对于自建的`k8s` 集群需要自己搭建一个负载均衡器来将外部流量引入集群内部，`MetalLB` 正好可以提供这类的功能。

## 部署过程

1. 下载 并部署`MetalLB` manifest, 这个manifest包含了很多crd资源。
```shell
wget https://raw.githubusercontent.com/metallb/metallb/v0.13.7/config/manifests/metallb-native.yaml

kubectl apply -f ./metallb-native.yaml

kubectl wait --namespace metallb-system  --for=condition=ready pod --selector=app=metallb --timeout=90s
```

2.  下载并部署MetalLB 配置文件.
```shell
wget https://kind.sigs.k8s.io/examples/loadbalancer/metallb-config.yaml
```


主要是配置ip 区间, 这里的ip 可以看做是用作你自建集群外部访问入口，是局域网IP
```yaml
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: example
  namespace: metallb-system
spec:
  addresses:
  - 172.20.0.100-172.20.0.150
---
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: empty
  namespace: metallb-system
```

如果你用的Kind 部署的`k8s` 集群， 可以从docker 管理IP 范围里选择一段IP 地址区间作为metallb 的备选ip范围， 获取docker IPAM command如下：

```shell
# assume kind docker network name is kind.
docker network inspect -f '{{.IPAM.Config}}' kind

# stdout->[{172.20.0.0/16  172.20.0.1 map[]} {fc00:f853:ccd:e793::/64  fc00:f853:ccd:e793::1 map[]}]
```

这样在Linux 环境下就可以以自动分配的loadbalance ip 访问集群内部服务了。

```text
default          foo-service            LoadBalancer   10.96.67.56     172.20.0.100   5678:31713/TCP                                                               7d5h
istio-system     istio-ingressgateway   LoadBalancer   10.96.55.172    172.20.0.101   15021:30880/TCP,80:32490/TCP,443:31912/TCP,31400:30886/TCP,15443:32434/TCP   6d2h
```
