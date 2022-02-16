#### 显示已经安装的包
```console
yum list installed
```

#### 查询哪个包包含指定文件
```console
yum provides "*/zlib"
```

#### centos8修改yum源
```console
minorver=8.5.2111
sudo sed -e "s|^mirrorlist=|#mirrorlist=|g" \
         -e "s|^#baseurl=http://mirror.centos.org/\$contentdir/\$releasever|baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos-vault/$minorver|g" \
         -i.bak \
         /etc/yum.repos.d/CentOS-*.repo
sudo yum makecache
```