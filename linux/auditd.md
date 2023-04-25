#### 查看进程被谁杀死了
[how-to-know-what-is-killing-vertica-process]https://forum.vertica.com/discussion/241701/how-to-know-what-is-killing-vertica-process


#### 审计系统调用
```console
auditctl -a exit,always -F arch=x86_64 -S mkdir -k name
ausearch -i -k name
```