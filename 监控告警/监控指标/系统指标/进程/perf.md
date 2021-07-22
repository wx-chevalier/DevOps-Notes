# perf

perf 是 linux 下一个非常强大的性能分析工具，通过它可以分析出进程运行过程中的主要时间都花在了哪些地方；结合著名的 [FlameGraph](https://github.com/brendangregg/FlameGraph.git) 火焰图工具，我们能够快速定位 时间占用较多的函数调用。

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
