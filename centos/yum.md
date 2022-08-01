#### 显示已经安装的包
```console
yum list installed
```

#### 查询哪个包包含指定文件
```console
yum provides "*/zlib"
```

#### 查询group信息
```console
yum groupinfo <groupname>
```

#### centos8修改yum源
建议先备份 /etc/yum.repos.d/ 内的文件。 
需要确定您所需要的小版本，如无特殊需要则使用该大版本的最后一个小版本，比如 6.10，5.11，我们将其标记为 $minorver，需要您在之后的命令中替换。
```console
minorver=8.5.2111
sudo sed -e "s|^mirrorlist=|#mirrorlist=|g" \
         -e "s|^#baseurl=http://mirror.centos.org/\$contentdir/\$releasever|baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos-vault/$minorver|g" \
         -i.bak \
         /etc/yum.repos.d/CentOS-*.repo
sudo yum makecache
```

#### 安装时默认选"y"
```console
# yum -y install xxx
# yum -y remove xxx
```

#### 更新
```console
# yum update xxx
```

#### List Enabled Yum Repositories
```console
# yum repolist
```

#### List all Enabled and Disabled Yum Repositories
```console
# yum repolist all
```

#### Install a Package from a Specific Repository
```console
# yum --enablerepo=epel install xxx
```

#### 下载包不安装
```console
# yum install --downloadonly --downloaddir=<path> <package>
```