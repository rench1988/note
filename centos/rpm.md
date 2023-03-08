#### 查询安装包包含的文件
```console
# rpm -ql{p} {packageName}
```

#### 查询指定文件属于哪个包
```console
# rpm -qf {filename}
```

#### 删除包但不删除依赖
```console
rpm -e --nodeps packageA
```

#### 查询包的依赖
```console
rpm -qp mypackage.rpm --requires
```


