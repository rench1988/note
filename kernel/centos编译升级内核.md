### 1. 下载源码
```wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.6.9.tar.sign```
```tar xvf linux-5.6.9.tar```

### 2. 配置内核feature
```cd linux-5.6.9```
```cp -v /boot/config-$(uname -r) .config```

### 3. 安装compiler和其它工具
```yum group install "Development Tools"```
```yum install ncurses-devel bison flex elfutils-libelf-devel openssl-devel```

### 4. 配置内核
```make menuconfig```

### 5. 编译内核
```make -j8```

### 6. 安装内核模块
```make modules_install```

### 7. 安装内核
```make install```

### 8. Update grub config
```grub2-mkconfig -o /boot/grub2/grub.cfg```
```grubby --set-default /boot/vmlinuz-5.6.9```