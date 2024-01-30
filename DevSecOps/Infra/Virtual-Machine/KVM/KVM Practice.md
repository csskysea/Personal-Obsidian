

# Resource adjustment


场景一: 虚拟机磁盘空间不足，需要扩容

Step 1: 关闭vm, 登入vm host上给虚拟机磁盘 resize

Step2: 启动vm, 进入vm, `fdisk` 分区(lvm),创建`pv` ,扩展`vg` , 扩展`lv` ,最后resize filesystem

- adjust kvm vm disk size.

pvcreate /dev/vda3
 1070  lsv
 1071  lvs
 1072  vgs
 1073  lvs
 1074  pvs
 1075  fdisk -l
 1076  partprobe
 1077  fdisk -l
 1078  df -h
 1079  lsblk
 1080  pvcreate /dev/vda3
 1081  pvs
 1082  vgs
 1083  vgextend centos /dev/vda3
 1084  vgs
 1085  lvs
 1086  vgdisplay
 1087  lvs
 1088  sudo lvs
 1089  lvextend -r -l +100%FREE /dev/centos/root
 1090  lvs
 1091  df -h
 1092  lsblk
 1093  blkid
 1094  xfs_growfs /dev/centos/root
```



磁盘 /dev/vda：375.8 GB, 375809638400 字节，734003200 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：dos
磁盘标识符：0x000c31b0

   设备 Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048     2099199     1048576   83  Linux
/dev/vda2         2099200   524287966   261094383+  8e  Linux LVM
/dev/vda3       524288000   734003199   104857600   83  Linux

磁盘 /dev/mapper/centos-root：265.2 GB, 265210036224 字节，517988352 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


磁盘 /dev/mapper/centos-swap：2147 MB, 2147483648 字节，4194304 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节

## Reference

https://www.howtogeek.com/devops/how-to-increase-a-kvm-virtual-machines-disk-size/

