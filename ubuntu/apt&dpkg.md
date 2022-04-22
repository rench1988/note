#### 查询已经安装的包
```console
apt list --installed (Ubuntu 14.04 and above)
dpkg --get-selections (old version)
```

#### 搜索包
```console
apt-cache search keyword
```

#### 查询包来自哪个rep
```console
apt-cache policy package-name
```

#### 查询包的详细信息
```console
apt-cache show package-name
```