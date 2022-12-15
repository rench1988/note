##### 1. 查看已经安装的虚拟机
```console
wsl --list -v
```

##### 2. 停止虚拟机
```console
wsl -t Ubuntu
```

##### 3. 导出虚拟机
```console
wsl --export Ubuntu "D:\wsl_export\ubuntu-ex.tar"
```

##### 4. 移除虚拟机
```console
wsl --unregister Ubuntu
```

##### 5. 导入虚拟机
```console
wsl --import Ubuntu "D:\wsl_import\ubuntu" "D:\wsl_export\ubuntu-ex.tar"
```