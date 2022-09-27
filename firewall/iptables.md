#### 查看所有策略
```console
# iptables -L -v
```

#### 修改默认策略
```console
# iptables --policy INPUT ACCEPT(DROP)
# iptables --policy OUTPUT ACCEPT(DROP)
# iptables --policy FORWARD ACCEPT(DROP)
```

#### 清除所有策略
```console
# iptables -F
```

#### 常见命令示例
```console
# iptables -A INPUT -s 10.10.10.10 -j DROP
# iptables -A INPUT -s 10.10.10.0/24 -j DROP
# iptables -A INPUT -s 10.10.10.0/255.255.255.0 -j DROP
# iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -j DROP
# iptables -A INPUT -p tcp --dport ssh -j DROP
# iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -m state --state NEW,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -p tcp --sport 22 -d 10.10.10.10 -m state --state ESTABLISHED -j ACCEPT
```

#### 显示每个rule的编号
```console
iptables -L --line-numbers
```

#### 删除rule
```console
iptables -D INPUT <line-number>
```
