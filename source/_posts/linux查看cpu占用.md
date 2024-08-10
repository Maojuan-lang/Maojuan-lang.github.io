---
title: linux查看cpu占用
date: 2024-08-10
---
```
查看cpu的占用情况，输入进程pid可以查看进程占用情况
htop
```

```
查看cpu的占用情况，按1展开各个核心的占用情况
top

us (user space)：表示用户空间的CPU使用百分比，即应用程序的CPU占用。
sy (system)：表示系统空间的CPU使用百分比，即内核的CPU占用。
ni (nice)：表示用户空间中调整过优先级的进程的CPU使用百分比。
id (idle)：表示CPU空闲时间的百分比，即CPU没有进行任何任务的时间。
wa (iowait)：表示CPU等待I/O操作完成的时间百分比。
hi (hardware interrupts)：表示处理硬件中断的CPU使用百分比。
si (software interrupts)：表示处理软件中断的CPU使用百分比。
st (steal)：表示虚拟化环境下，其他虚拟机对CPU的占用时间百分比。

PID: 进程ID（Process ID）
USER: 进程所有者的用户名（User）
PR: 进程优先级（Priority）
NI: 进程的“nice”值（Nice value），影响进程的优先级
VIRT: 进程使用的虚拟内存总量（Virtual Memory Size）
RES: 进程使用的物理内存总量（Resident Set Size）
SHR: 进程共享的内存总量（Shared Memory Size）
S: 进程状态（State），如S代表休眠（Sleeping），R代表运行（Running）
%CPU: 进程使用的CPU百分比（CPU Usage）
%MEM: 进程使用的内存百分比（Memory Usage）
TIME+: 进程总共使用的CPU时间（CPU Time） 格式MM:SS.s
COMMAND: 启动进程的命令（Command）
```

```
每隔一秒查看cpu使用情况 Virtual Memory Statistics
vmstat 1

r: 运行队列中等待运行的进程数（Running）
b: 在等待I/O操作的进程数（Blocked）
swpd: 使用的交换空间总量（Swap Used）
free: 空闲的内存总量（Free Memory）
buff: 用作缓存的内存总量（Buffered Memory）
cache: 用作文件缓存的内存总量（Cached Memory）
si: 从交换空间到内存的数据传输速度（Swap In）
so: 从内存到交换空间的数据传输速度（Swap Out）
bi: 从块设备读取的数据量（Block In）
bo: 写入到块设备的数据量（Block Out）
in: 每秒中断的次数（Interrupts）
cs: 每秒上下文切换的次数（Context Switches）
us: 用户空间使用的CPU百分比（User Space CPU）
sy: 系统空间使用的CPU百分比（System CPU）
id: CPU空闲百分比（Idle CPU）
wa: 等待I/O操作的CPU百分比（I/O Wait）
st: 虚拟化环境中，其他虚拟机占用的CPU百分比（Steal Time）
```

```
每隔一秒查看cpu使用情况
sar -u 1
```

```
每隔一秒查看cpu各个核心使用情况 Multiprocessor Statistics
mpstat -P ALL 1
```

```
每隔一秒查看用户空间cpu占比
pidstat -u 1
```

