### 魔方云安装完毕后几点优化操作 以及常见问题处理

1.安装魔方云中间速度特别慢
解决方案

```
vi /etc/hosts
```

添加一行

```
43.248.188.22 mirror.cloud.idcsmart.com
```

如果速度仍然卡慢 itdog ping一下mirror.cloud.idcsmart.com 选择一个合适的节点添加hosts
vi 或者 hosts 不会用 就rm -rf跑路吧

2.安装完毕魔方云之后 需要开启KSM内存回收 以及添加swap
2.1 开启KSM

```
systemctl start ksm ksmmgr
```

没有回复就算没问题了

2.2 设置SWAP
2.2.1 添加SWAP内存

```
fallocate -l 200G /home/swap #这一步是添加SWAP内存 200G是容量 /home/swap是文件容量
mkswap /home/swap 写入SWAP
swapon /home/swap 挂载SWAP

编辑 /etc/fstab vi /etc/fstab
添加一行 /home/swap swap swap defaults 0 0
```

保存即可

2.2.2 设置SWAP调度

```
vi /etc/sysctl.conf
添加一行 vm.swappiness=100
100为 优先使用SWAP
0为不使用SWAP 建议磁盘优秀者（U2，SSD阵列）使用100 SAS阵列使用10-90 单机械硬盘用你妈SWAP 跑路吧穷逼
```

保存即可

