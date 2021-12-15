### 配置项
```console
[root@localhost ~]# sysctl kernel.core_pattern
kernel.core_pattern = |/usr/lib/systemd/systemd-coredump %P %u %g %s %t %c %h %e
```

配置文件名的可用指示符
>%%  a single % character  
%p  PID of dumped process  
%u  (numeric) real UID of dumped process  
%g  (numeric) real GID of dumped process  
%s  number of signal causing dump  
%t  time of dump, expressed as seconds since the Epoch (00:00h, 1 Jan 1970, UTC)  
%h  hostname (same as nodename returned by uname(2))  
%e  executable filename (without path prefix)  
%c  core file size soft resource limit of crashing process (since Linux 2.6.24)  


### 配置core文件名
```console
# sysctl -w kernel.core_pattern="%e-%t.core"
```

将配置持久化
```console
# echo 'kernel.core_pattern="%e-%t.core"' >> /etc/sysctl.conf
# sysctl -p
```
