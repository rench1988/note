### Thread stop
[Thread stop](https://sourceware.org/gdb/onlinedocs/gdb/Thread-Stops.html#Thread-Stops)

### 设置反汇编代码格式
```console
set disassembly-flavor intel
```

### 打印具体地址的值 
```console
(gdb) help x
Examine memory: x/FMT ADDRESS.
ADDRESS is an expression for the memory address to examine.
FMT is a repeat count followed by a format letter and a size letter.
Format letters are o(octal), x(hex), d(decimal), u(unsigned decimal),
  t(binary), f(float), a(address), i(instruction), c(char), s(string)
  and z(hex, zero padded on the left).
Size letters are b(byte), h(halfword), w(word), g(giant, 8 bytes).
The specified number of objects of the specified size are printed
according to the format.  If a negative number is specified, memory is
examined backward from the address.

Defaults for format and size letters are those previously used.
Default count is 1.  Default address is following last thing printed
with this command or "print".

(gdb) x/t 0x404030 (t表示二进制方式)
0x404030 <v1>:  11001101

(gdb) x/4t 0x404030 (4表示后面的4个字节都打印)
0x404030 <v1>:  11001101        11001100        10001100        00111111

(gdb) x/tw 0x404030 (w表示打印一个word，一个word在gdb中默认为4byte)
0x404030 <v1>:  00111111100011001100110011001101 (注意字节序)
```