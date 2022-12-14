#### kernel的时钟频率
```console
grep 'CONFIG_HZ=' /boot/config-$(uname -r) 
```
CONFIG_HZ=250 means 250 interrupts are triggered per second (1 interrupt every 4 milliseconds)

#### pidstat命令

