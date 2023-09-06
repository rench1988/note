#### 查看系统启动消耗时间
```
systemd-analyze time
```

#### 查看各个服务启动消耗时间
```
systemd-analyze critical-chain  或者 systemd-analyze blame
```
