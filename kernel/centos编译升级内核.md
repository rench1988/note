[原文链接](https://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)

### 1. 下载源码
```console
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.6.9.tar.sign
tar xvf linux-5.6.9.tar
```

### 2. 配置内核feature
```console
cd linux-5.6.9
cp -v /boot/config-$(uname -r) .config
```

### 3. 安装compiler和其它工具
```console
yum group install "Development Tools"
yum install ncurses-devel bison flex elfutils-libelf-devel openssl-devel
```

### 4. 配置内核
```console
make menuconfig
```

### 5. 编译内核
```console
make -j8
```

### 6. 安装内核模块
```console
make modules_install
```

### 7. 安装内核
```console
make install
```

### 8. Update grub config
```console
grub2-mkconfig -o /boot/grub2/grub.cfg
grubby --set-default /boot/vmlinuz-5.6.9
```