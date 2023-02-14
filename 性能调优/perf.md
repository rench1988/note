#### perf源码下载地址
https://mirrors.edge.kernel.org/pub/linux/kernel/tools/perf/<br/>
系统自带的或者用yum安装的perf不支持python, 要自己手动编译出程序

#### record performance data
```console
perf record -p `pidof a.out`
```

to record for 10 secs
```console
perf record -p `pidof a.out` sleep 10
```

to record with call graph
```console
perf record -g -p `pidof a.out` 
```

指定输出
```console
perf record -g  -p `pidof my_test` -o ./my_test.perf.data sleep 30
```

#### analyze performance data
analyze load per module:
```console
perf report --stdio -g none --sort comm,dso -i ./my_test.perf.data
```

per function is analyzed
```console
perf report --stdio -g none -i ./my_test.perf.data | c++filt
```

call chains are analyzed
```console
perf report --stdio -g graph -i ./my_test.perf.data | c++filt
```

#### 查看程序的符号名
```console
perf probe –x ./load --funcs
perf probe -x tst --funcs --no-demangle --filter '*'  (probe c++函数时使用)
```

#### 添加函数进入事件
```console
perf probe –x ./load main
perf probe -x tst --add _ZN1N1fEi --no-demangle (probe c++函数时使用)
perf probe -x myelf --add myalias=_SomeVeryLongMangledNameWhee (c++函数名过长时)
```

#### 添加函数退出事件
```console
perf probe –x ./load main%return
perf probe -x tst --add _ZN1N1fEi%return (probe c++函数时使用)
```

#### 查询trace-point事件
```console
perf probe -v --line  _ZN7CDBOper10ExecuteSQLEP11otl_connectiRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEE -x ./program  (查询trace-point对应的代码行号)
```
