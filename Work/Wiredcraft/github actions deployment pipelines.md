
## Solutions

主要利用github actions 结合 `kustomize` 和 `sealedsecrets` 来实现在github repo 中手动部署Omni 各个业务服务组件。

## 主要维护工作

针对每个业务微服务

- 所有涉及到的K8s资源 manifests , kustomize 的维护
- 所有configmap, sealedsecrets的维护

## 问题记录

1. 怎么部署`k8s job` ?
 因为 `k8s job` 是immuteable, 重复部署会报错，必须手动删除job，在运行pipelines才能成功。
 2. 需要统一 `docker image  路径
  用github actions部署的时候 依赖manual dispatch 传入image 信息会比较麻烦
  不同微服务image 命名格式，aliyun registry path , 甚至有个别component 存在多个image
  目前定义比较混乱，wiredcraft registry 和aliyun image repo path 定义需要统一，否则很难做到从外部指定版本来部署。
3. 当`configmap` update的时候怎么让Pod reload。


## Scope

此部署方案只限用于部署业务应用服务, 不会涉及基础设施setup, 一些`k8s manifests` 中部分依赖项譬如  `pv,pvc,pullsecrets`  这些也需要提前准备好。