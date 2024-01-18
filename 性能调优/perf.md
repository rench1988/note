#### perf源码下载地址
https://mirrors.edge.kernel.org/pub/linux/kernel/tools/perf/<br/>
系统自带的或者用yum安装的perf不支持python, 要自己手动编译出程序

#### record performance data
```console
# perf record -p `pidof a.out`
```

to record for 10 secs
```console
# perf record -p `pidof a.out` sleep 10
```

to record with call graph
```console
# perf record -g --call-graph dwarf -p `pidof a.out` 
```

指定输出
```console
# perf record -g  -p `pidof my_test` -o ./my_test.perf.data sleep 30
```

#### analyze performance data
analyze load per module:
```console
# perf report --stdio -g none --sort comm,dso -i ./my_test.perf.data
```

per function is analyzed
```console
# perf report --stdio -g none -i ./my_test.perf.data | c++filt
```

call chains are analyzed
```console
# perf report --stdio -g graph -i ./my_test.perf.data | c++filt
```

#### 查看程序的符号名
```console
# perf probe –x ./load --funcs
# perf probe -x tst --funcs --no-demangle --filter '*'  (probe c++函数时使用)
```

#### 添加函数进入事件
```console
# perf probe –x ./load main
# perf probe -x tst --add _ZN1N1fEi --no-demangle (probe c++函数时使用)
# perf probe -x myelf --add myalias=_SomeVeryLongMangledNameWhee (c++函数名过长时)
```

#### 添加函数退出事件
```console
# perf probe –x ./load main%return
# perf probe -x tst --add _ZN1N1fEi%return (probe c++函数时使用)
```

#### 查询添加的函数
```console
# perf probe -l
probe_HAgent:MultiAuthRequest (on MultiAuthRequest@./src/HAgentFTSRecv.cpp in /home/leagsoft/SafeDataExchange/Bin/HAgent)
probe_HAgent:MultiAuthRequest__return (on MultiAuthRequest%return@./src/HAgentFTSRecv.cpp in /home/leagsoft/SafeDataExchange/Bin/HAgent)
```

#### 查询trace-point事件
```console
# perf probe -v --line  _ZN7CDBOper10ExecuteSQLEP11otl_connectiRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEE -x ./program  (查询trace-point对应的代码行号)
```

#### perf脚本示例
```console
from __future__ import print_function
  
import os
import sys

sys.path.append(os.environ['PERF_EXEC_PATH'] + '/scripts/python/Perf-Trace-Util/lib/Perf/Trace')

from perf_trace_context import *
from Core import *

statDict = {}

def trace_begin():
    print("in trace_begin")


def trace_end():
    print("in trace_end")

def func_start(event_name, tid, common_secs, common_nsecs):
    global statDict
    if tid not in statDict:
        statDict[tid] = {}

    statDict[tid][event_name] = (common_secs * 1000) + (common_nsecs / 1000000)

def func_end(event_name, tid, common_secs, common_nsecs):
    global statDict
    event_name_start = event_name[:-8]
    if tid not in statDict:
        print("Warn: tid %d func %s, tid not find" %(tid, event_name))
        return

    eventDict = statDict[tid]
    if event_name_start not in eventDict:
        print("Warn: tid %d func %s %s, func not find" %(tid, event_name, event_name_start))
        return

    nowMills = (common_secs * 1000) + (common_nsecs / 1000000)
    diff = nowMills - statDict[tid][event_name_start]
    print("tid %d func %s running %u" %(tid, event_name_start, diff))

def trace_unhandled(event_name, context, event_fields_dict, perf_sample_dict):
    print(get_dict_as_string(event_fields_dict))
    print('Sample: {'+get_dict_as_string(perf_sample_dict['sample'], ', ')+'}')

# event名为probe_HAgent:MultiAuthRequest
def probe_HAgent__MultiAuthRequest(event_name, context, common_cpu, common_secs, common_nsecs, common_pid, common_comm, comm, pid):
    func_start(event_name, common_pid, common_secs, common_nsecs)
    print("%s %u %u" %(event_name, pid, common_pid))

# event名为probe_HAgent:MultiAuthRequest__return
def probe_HAgent__MultiAuthRequest__return(event_name, context, common_cpu, common_secs, common_nsecs, common_pid, common_comm, comm, pid, unknown):
    func_end(event_name, common_pid, common_secs, common_nsecs)
    print("%s %u %u" %(event_name, pid, common_pid))

def print_header(event_name, cpu, secs, nsecs, pid, comm):
    print("%-20s %5u %05u.%09u %8u %-20s " % (event_name, cpu, secs, nsecs, pid, comm), end="")

def get_dict_as_string(a_dict, delimiter=' '):
    return delimiter.join(['%s=%s'%(k,str(v))for k,v in sorted(a_dict.items())])        
```
