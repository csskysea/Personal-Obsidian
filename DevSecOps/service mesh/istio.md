#k8s #kubernetes #service-mesh

## What's istio?

> [Istio](https://istio.io/latest/docs/concepts/what-is-istio/) is an open platform for providing a uniform way to [integrate microservices](https://istio.io/latest/docs/examples/microservices-istio/), manage [traffic flow](https://istio.io/latest/docs/concepts/traffic-management/) across microservices, enforce policies and aggregate telemetry data. Istio's control plane provides an abstraction layer over the underlying cluster management platform, such as Kubernetes.

## Architectures

## Which components contained?

- **Envoy** - Sidecar proxies per microservice to handle ingress/egress traffic between services in the cluster and from a service to external services. The proxies form a _secure microservice mesh_ providing a rich set of functions like discovery, rich layer-7 routing, circuit breakers, policy enforcement and telemetry recording/reporting functions.
    
    > Note: The service mesh is not an overlay network. It simplifies and enhances how microservices in an application talk to each other over the network provided by the underlying platform.
    
- **Istiod** - The Istio control plane. It provides service discovery, configuration and certificate management. It consists of the following sub-components:
    
    - **Pilot** - Responsible for configuring the proxies at runtime.
        
    - **Citadel** - Responsible for certificate issuance and rotation.
        
    - **Galley** - Responsible for validating, ingesting, aggregating, transforming and distributing config within Istio.
        
- **Operator** - The component provides user friendly options to operate the Istio service mesh.

##  service mesh 解决哪些问题？

传统的单体应用被拆分成很多的微服务在解耦的同时也带来了更多的复杂性，众多的微服务间的通信需要去关注和治理，服务发现，路由，重试和故障转移都需要处理。

- 流量控制
- 流量安全
- 可观测性

## How to setup istio?

### Prerequisite

- have an available  `k8s` cluster. 
     here we use a ready `k8s` which was setup with `kind` .

- loadbalancer for istio gateway.([[metalLB]])
     setup `[metalLB]` beforehand, we use its layer 2 load balancer function for external network access.
```shell
kubectl apply -f https://raw.githubusercontent.com/[[metallb]]/[[metallb]]/v0.13.7/config/manifests/[[metallb]]-native.yaml
```


### Procedures 

1. download `istioctl` ,extract it and add the `bin` directory in which `istioctl` is  to `PATH` env var.
here we choose `istioctl` to setup istio service mesh to `k8s`, you can choose other way such as helm chart accordingly.
```shell
# will download the latest version in default, so you can specify a version for it.
curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.20.2 TARGET_ARCH=x86_64 sh -


```
3. setup `istio` service mesh to `k8s` with `istioctl`.
```shell
# here we use the demo profile for test.it will install istio-core, istiod,ingress gateway,egress gateway compoents.
istioctl install --set profile=demo -y
```
4. label namepace which need to be managed  by `istio` service mesh.
```shell

# only pods in the namespace which has the label would be inject istio envoy proxy container.
kubectl label namespace default istio-injection=enabled
```




## Tutorial

### `istio` api 

- gateway
	you can use one of the following:
	- `istio` ingress gateway
	- k8s standard gateway api 
	    need to setup beforehand:
	    ```shell
	   kubectl get crd gateways.gateway.networking.k8s.io &> /dev/null || \
  { kubectl kustomize "github.com/kubernetes-sigs/gateway-api/config/crd?ref=v1.0.0" | kubectl apply -f -; }

      ```
- virtualservices
- destinationrules
##  Reference

1. https://githubfast.com/csskysea/istio
2. 