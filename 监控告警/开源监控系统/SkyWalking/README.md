# SkyWalking

官方给 SkyWalking 的定义是一个分布式系统的应用程序性能监视工具，也是一个开源的可观测平台, 用于从服务和云原生基础设施收集、 分析、 聚合及可视化数据。SkyWalking 提供了一种简便的方式来清晰地观测分布式系统, 甚至横跨多个云平台。SkyWalking 更是一个现代化的应用程序性能监控(Application Performance Monitoring)系统, 尤其专为云原生、基于容器的分布式系统设计。

## SkyWalking 的功能

SkyWalking 在官方文档中给出了如下功能：

- 多种监控手段。可以通过语言探针和 service mesh 获得监控是数据。
- 多个语言自动探针。包括 Java，.NET Core 和 Node.JS。
- 轻量高效。无需大数据平台，和大量的服务器资源。
- 模块化。UI、存储、集群管理都有多种机制可选。
- 支持告警。
- 优秀的可视化解决方案。

作为一个 APM 工具，这些功能应该还挺实用的。不过还没有开始使用 SkyWalking，这些功能等使用过了再进行讲解。

## SkyWalking 的使用场景

在许多不同的场景下, SkyWalking 为观察和监控分布式系统提供了解决方案。首先是像传统的方式那样, SkyWalking 为服务提供了自动打点的代理, 如 Java, C# , Node.js , Go , PHP 以及 Nginx LUA（包括 Python 和 C++ 调用的 SDK 捐献）。对于多数语言，持续部署环境，云原生基础设施正变得更加强大，但也更加复杂。Skywalking 的服务网格接收器可以让 Skywalking 接收来自服务网格框架（例如 Istio , Linkerd）的遥测数据，以帮助用户理解整个分布式系统。

总之, SkyWalking 为 服务(service), 服务实例(service instance), 以及 端点(endpoint) 提供了可观测能力。服务(Service), 实例(Instance) 以及 端点(Endpoint) 等概念在如今随处可见, 所以让我们先了解一下他们在 SkyWalking 中都表示什么意思：

- 服务(Service). 表示对请求提供相同行为的一组工作负载. 在使用打点代理或 SDK 的时候,你可以定义服务的名字. SkyWalking 还可以使用在 Istio 等平台中定义的名称。
- 服务实例(Service Instance). 上述的一组工作负载中的每一个工作负载称为一个实例. 就像 Kubernetes 中的 pods 一样,服务实例未必就是操作系统上的一个进程. 但当你在使用打点代理的时候, 一个服务实例实际就是操作系统上的一个真实进程.
- 端点(Endpoint). 对于特定服务所接收的请求路径, 如 HTTP 的 URI 路径和 gRPC 服务的类名 + 方法签名。

使用 SkyWalking 时, 用户可以看到服务与端点之间的拓扑结构, 每个服务/服务实例/端点的性能指标, 还可以设置报警规则。除此之外, 你还可以通过以下方式集成

- 其他分布式追踪使用 Skywalking 原生代理和 Zipkin , Jaeger 和 OpenCensus 的 SDK；
- 其他度量指标系统，例如 Prometheus, Sleuth, Micrometer。
