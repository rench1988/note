### 配置项
```console
[root@localhost ~]# cat /proc/sys/net/ipv4/tcp_keepalive_time 
7200
[root@localhost ~]# cat /proc/sys/net/ipv4/tcp_keepalive_intvl
75
[root@localhost ~]# cat /proc/sys/net/ipv4/tcp_keepalive_probes 
9
```

### 配置值
```console
# vi /etc/sysctl.conf
net.ipv4.tcp_keepalive_time = 60
net.ipv4.tcp_keepalive_intvl = 10
net.ipv4.tcp_keepalive_probes = 6
# sysctl -p
```

### 参数解释
* net.ipv4.tcp_keepalive_time = 60  
网络保持inactive的时间超过60s开始发送第一个keepalive数据包

* net.ipv4.tcp_keepalive_intvl = 10  
每隔10s发送一个keepalive数据包

* net.ipv4.tcp_keepalive_probes = 6  
连续发送6次keepalive数据包都没有收到响应，则认为该tcp连接已经断开

结合上面的配置，应用程序会在120s后感知到tcp连接已经断开(60 + 10 + 10 + 10 + 10 + 10 + 10)