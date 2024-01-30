

## Architecture

![[Pasted image 20240117100228.png]]
## Redis 解决那些问题？


## Redis 部署方式有哪些，针对哪些场景？

- single master node mode 
		- simple and efficient.
- sentinel master slave mode 
	    - master replica data to slaves.
	    - each node has the whole data.
	    - generally client read&write on master node, but only read on slave nodes.
	    - when old master node can't work, the system will elect a new master (most count nodes agree quorum)
- redis cluster mode
		- when can't load the whole  data on one single node.
		- sharding, each node instance has partial data, for high availability, the system may have multiple sharding replication on different node.

## Redis 生产实践中可能碰到的问题及对策

- 避免key 集中过期。
- 避免key的值占用内存过大,俗称的大key。

