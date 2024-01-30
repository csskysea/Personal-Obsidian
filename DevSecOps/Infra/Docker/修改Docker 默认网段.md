#docker
#infra

### 背景

Docker 安装好之后默认开启的是172开头的网段，这个网段如果与公司的网段相同就会导致冲突,因此有必要修改docker的网段。

### 怎么做

```

#create daemon.json in /etc/docker

#add the following, eg. add 10.10.0.0/16 subnet

{

"default-address-pools":

[

{"base":"10.10.0.0/16","size":24}

]

}

```

then restart docker engine.

```

systemctl restart docker.

```

### 验证是否生效

```

# check output of system route.

ip route

```
