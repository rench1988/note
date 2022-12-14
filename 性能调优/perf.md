[原文](https://stackoverflow.com/questions/2229336/linux-application-profiling)

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