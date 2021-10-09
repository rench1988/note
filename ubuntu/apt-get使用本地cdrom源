```mkdir /media/cdrom

#mount 挂载镜像到本地目录
mount -t iso9660 -o loop /dev/sr0 /media/cdrom (或者：mount -t auto /dev/cdrom /media/cdrom)

#添加本地目录到软件源
sudo apt-cdrom -m -d=/media/cdrom add

#查看apt源地址, 可以将在线源删除，仅保留本地源
cat /etc/apt/sources.list```