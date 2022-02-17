#### 1. 挂载本地dvd
```console
# mount /dev/sr0 /media/iso/
```

#### 2. 拷贝media.repo到/etc/yum.repos.d/
```console
# cp -v /media/iso/media.repo  /etc/yum.repos.d/centos8.repo
```

#### 3. 修改centos8.repo
```console
# vim etc/yum.repos.d/centos8.repo
[InstallMedia-BaseOS]
name=CentOS Linux 8 - BaseOS
metadata_expire=-1
gpgcheck=1
enabled=1
baseurl=file:///media/iso/BaseOS/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
```

#### 4. 清除yum缓存
```console
# yum clean all
```

#### 5. 查看启用的repolist
```console
# yum repolist
```
不想使用的repo可以将其enabled置为0

