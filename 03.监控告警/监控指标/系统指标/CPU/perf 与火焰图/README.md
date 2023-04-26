# perf

perf 是 linux 下一个非常强大的性能分析工具，通过它可以分析出进程运行过程中的主要时间都花在了哪些地方。它是 Linux 系统原生提供的性能分析工具，会返回 CPU 正在执行的函数名以及调用栈（stack）。通常，它的执行频率是 99Hz（每秒 99 次），如果 99 次都返回同一个函数名，那就说明 CPU 这一秒钟都在执行同一个函数，可能存在性能问题。

```sh
$ sudo perf record -F 99 -p 13204 -g -- sleep 30
```

上面的代码中，perf record 表示记录，-F 99 表示每秒 99 次，-p 13204 是进程号，即对哪个进程进行分析，-g 表示记录调用栈，sleep 30 则是持续 30 秒。运行后会产生一个庞大的文本文件。如果一台服务器有 16 个 CPU，每秒抽样 99 次，持续 30 秒，就得到 47,520 个调用栈，长达几十万甚至上百万行。

结合著名的 [FlameGraph](https://github.com/brendangregg/FlameGraph.git) 火焰图工具，我们能够快速定位时间占用较多的函数调用。

```sh
# 执行采样
$ perf record -e cpu-clock -g -p ${PID}

# 用 perf script 工具对 perf.data 进行解析
perf script -i perf.data &> perf.unfold

# 将 perf.unfold 中的符号进行折叠
./stackcollapse-perf.pl perf.unfold &> perf.folded

# 生成 svg 火焰图
/flamegraph.pl perf.folded > perf.svg
```
