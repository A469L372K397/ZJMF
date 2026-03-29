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

3.魔方云系统获取不到CPU和内存数据
3.1 数据库/自动任务 歇逼了
```
母鸡运行
systemctl restart crond #这是crond自动任务歇逼了
systemctl restart influxdb #这是记录数据的influxdb数据库歇逼了
```
3.2 PHP歇逼了
```
母鸡运行
/usr/bin/php /usr/local/zjmf/php/oneMinute.php
如果出现类似gd字样的报错 将报错的扩展通过yum的命令remove 再install 即可
```
4.出现主控连不上母鸡
首先 主控ping母鸡 检查互通问题
如果通的话 检查4432端口是否通
如果4432端口不通 或https://IP:4432 无法访问
```
systemctl restart php-fpm
systemctl restart httpd
```
如果是母鸡负载过高 那就跑路吧 php都起不来 跑路吧 穷逼

5.母鸡IP频繁被摸出来
通过iptables限制4432端口 指定IP访问
```
sudo iptables -I INPUT -p tcp --dport 4432 -s 1.1.1.1 -j ACCEPT
sudo iptables -I INPUT 2 -p tcp --dport 4432 -j DROP
```
6.CentOS出现 xmrig等挖矿软件
排除弱密码情况 首先需要更新yum源 然后``` yum -y install openssh openssl ```

更新一下OpenSSH即可

7.yum源更新失败
```
rm -rf /etc/yum.repos.d/*
```
再进行linuxmirrors即可

8 多IP转发报错 节点无法链接转发鸡
登录母鸡 输入```ssh root@IP #IP是转发机的IP```

密码在魔方云转发机的管理页面查看

出现SSH无法握手的情况 自行百度解决 改一下SSH进程文件即可

出现SSH密码错误 请联系机房 一般情况是机房做了一些内网策略导致的（例如成都中立机房） 联系机房解除即可
