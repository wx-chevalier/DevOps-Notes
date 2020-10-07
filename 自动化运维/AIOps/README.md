# AIOps

在数据采集阶段，保留了 Open-Faclon、CAT、客户端 SDK、Logstash 等入口，通过 Kafka 进行汇聚，引入大数据实时计算平台 Flink，提炼 metric 指标，并最终入库。

![](https://ww1.sinaimg.cn/large/007rAy9hgy1g0f3i634lsj30u00jwabs.jpg)

在告警方面，开发了 Alert Manager 组件，对接多种告警渠道：钉钉、短信、微信等，并且自动创建 Jira，告警闭环。
