#### 查看系统启动消耗时间
```
systemd-analyze time
```

#### 查看各个服务启动消耗时间
```
systemd-analyze critical-chain  或者 systemd-analyze blame
```

#### unit文件所处目录的优先级
```
1. /etc/systemd/system(最高优先级)
2. /run/systemd/system
3. /lib/systemd/system
```