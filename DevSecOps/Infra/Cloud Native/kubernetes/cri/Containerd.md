

`Containerd` 是`k8s` 生态中的一种容器运行时实现，作为Docker 的主要继任者。
在每个集群节点上部署。


进程调用链：

`containerd` -> `containerd-shim-runc-v2 -namespace k8s.io -id 3a3828ec32303746cd79cc51c0835cf4c869f5f6b9892385d43f6e187a378211 -address /run/containerd/containerd.sock`-> pod 容器进程(包括集群控制平面的进程)

这里 `containerd-shim-runc-v2` 参数 `-id` 是 运行在该节点上的pod 的id，可以通过

```shell
crictl ps 
```
查看。
==注： `crictl` 类似于 `docker` 客户端，命令相似，这里作为客户端与`containerd` 交互。==