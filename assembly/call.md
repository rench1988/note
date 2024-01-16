##### 相对近调用地址计算
```console
00E79E00  | E8 AE580000   CALL    someprocess.00E7F6B3
00E79E05  | 85C0          TEST    EAX, EAX
(output taken from OllyDbg)

00E79E05    (EIP)
+   58AE    (OFFSET)
--------
00E7F6B3    (目标函数的地址)

```
