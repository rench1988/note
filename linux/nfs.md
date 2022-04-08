#### 查看nfs客户端当前的挂载参数设置
```console
nfsstat -m
```

#### mount的常规option
```console
nfsvers=3,rsize=65535,wsize=65535,soft,timeo=30,retry=3
```

#### 查询挂载点stats
```console
mountstats /path/
```