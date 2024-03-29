# Google SRE 黄金指标

当我们设计复杂系统时，生产环境系统的可观察性是必须的，期望通过观察告诉我们什么时候，哪里出现了问题。

- 平时了解服务运行状况。
- 异常时，可发现服务故障，并定位故障原因。
- 事后，对异常点做分析，看是否在高峰期发生，或者持续更久，是否会出事故，如何解决。

Four Golden Signals 是 Google 针对大量分布式监控的经验总结，4 个黄金指标可以在服务级别帮助衡量终端用户体验、服务中断、业务影响等层面的问题。观察那些指标，按照《SRE：Google 运维解密》中描述的，监控的四个黄金指标如后： 延迟、流量、错误、饱和度。

![黄金指标示意](https://assets.ng-tech.icu/superbed/2021/07/22/60f985f25132923bf80a49cf.jpg)

这四类监控指标，在具体的业务和基础设施、中间件场景，要监控的项各有不同：

|          | 基础设施                                                                    | 业务监控                                                                                                                                                                                    |
| -------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 错误类   | 宕机；磁盘（坏盘或文件系统错误）；进程或端口挂掉；网络丢包；                | 错误日志;业务状态码、错误码走势;                                                                                                                                                            |
| 延迟类   | IO 等待；网络延迟；                                                         | 接口、服务的平均耗时、TP90、TP99、TP999 等；DB、缓存的慢查询；                                                                                                                              |
| 流量类   | 网络和磁盘 IO；                                                             | 服务层面的 QPS、PV 和 UV；各状态业务订单 TPM；针对音频流媒体系统来说，这个指标可能是网络 I/O 速率，或者并发会话数量；针对键值对存储系统来说，指标可能是每秒交易数量，或每秒的读取操作数量； |
| 饱和度类 | 系统资源利用率：CPU、内存、磁盘、网络等；饱和度：等待线程数，队列积压长度； | 该服务是否可以正常处理两倍的流量，是否可以应对 10%的额外流量，或者甚至应对当前更少的流量？预测：看起来数据库会在 4 个小时内填满硬盘；                                                       |

![Google SRE 黄金指标](https://assets.ng-tech.icu/item/20230418224219.png)

- 延迟：服务请求所需时间。记录用户所有请求所需的时间，重点是要区分成功请求的延迟时间和失败请求的延迟时间。例如在数据库或者其他关键祸端服务异常触发 HTTP 500 的情况下，用户也可能会很快得到请求失败的响应内容，如果不加区分计算这些请求的延迟，可能导致计算结果与实际结果产生巨大的差异。除此以外，在微服务中通常提倡“快速失败”，开发人员需要特别注意这些延迟较大的错误，因为这些缓慢的错误会明显影响系统的性能，因此追踪这些错误的延迟也是非常重要的。

- 通讯量：监控当前系统的流量，用于衡量服务的容量需求。流量对于不同类型的系统而言可能代表不同的含义。例如，在 HTTP REST API 中, 流量通常是每秒 HTTP 请求数；

- 错误：监控当前系统所有发生的错误请求，衡量当前系统错误发生的速率。对于失败而言有些是显式的(比如, HTTP 500 错误)，而有些是隐式(比如，HTTP 响应 200，但实际业务流程依然是失败的)。对于一些显式的错误如 HTTP 500 可以通过在负载均衡器(如 Nginx)上进行捕获，而对于一些系统内部的异常，则可能需要直接从服务中添加钩子统计并进行获取。

- 饱和度：衡量当前服务的饱和度。主要强调最能影响服务状态的受限制的资源。例如，如果系统主要受内存影响，那就主要关注系统的内存状态，如果系统主要受限与磁盘 I/O，那就主要观测磁盘 I/O 的状态。因为通常情况下，当这些资源达到饱和后，服务的性能会明显下降。同时还可以利用饱和度对系统做出预测，比如，“磁盘是否可能在 4 个小时候就满了”。

# RED 方法

RED 方法是 Weave Cloud 在基于 Google 的“4 个黄金指标”的原则下结合 Prometheus 以及 Kubernetes 容器实践，细化和总结的方法论，特别适合于云原生应用以及微服务架构应用的监控和度量。主要关注以下三种关键指标：

- (请求)速率：服务每秒接收的请求数。
- (请求)错误：每秒失败的请求数。
- (请求)耗时：每个请求的耗时。

在“4 大黄金信号”的原则下，RED 方法可以有效的帮助用户衡量云原生以及微服务应用下的用户体验问题。

# USE 方法

USE 方法全称"Utilization Saturation and Errors Method"，主要用于分析系统性能问题，可以指导用户快速识别资源瓶颈以及错误的方法。正如 USE 方法的名字所表示的含义，USE 方法主要关注与资源的：使用率(Utilization)、饱和度(Saturation)以及错误(Errors)。

- 使用率：关注系统资源的使用情况。这里的资源主要包括但不限于：CPU，内存，网络，磁盘等等。100%的使用率通常是系统性能瓶颈的标志。
- 饱和度：例如 CPU 的平均运行排队长度，这里主要是针对资源的饱和度(注意，不同于 4 大黄金信号)。任何资源在某种程度上的饱和都可能导致系统性能的下降。
- 错误：错误计数。例如：“网卡在数据包传输过程中检测到的以太网网络冲突了 14 次”。

通过对资源以上指标持续观察，通过以下流程可以知道用户识别资源瓶颈：

![img](https://gblobscdn.gitbook.com/assets%2F-LBdoxo9EmQ0bJP2BuUi%2F-LPS8LQB5PdyyY0X1z6h%2F-LPS8NI0J-F_01SeCTRB%2FUSEMethod.png?alt=media)
