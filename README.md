[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![license: CC BY-NC-SA 4.0](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-lightgrey.svg)][license-url]

<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/wx-chevalier/DevOps-Series">
    <img src="https://s2.ax1x.com/2020/01/23/1V2lA1.png" alt="Logo" width="150" height="80">
  </a>

  <h3 align="center">DevOps Series</h3>

  <p align="center">
    软件开发与部署
    <br />
    <a href="https://github.com/wx-chevalier/DevOps-Series"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/wx-chevalier/DevOps-Series">View Demo</a>
    ·
    <a href="https://github.com/wx-chevalier/DevOps-Series/issues">Report Bug</a>
    ·
    <a href="https://github.com/wx-chevalier/DevOps-Series/issues">Request Feature</a>
  </p>
</p>

<!-- ABOUT THE PROJECT -->

# Introduction | 前言

![概念图](https://i.postimg.cc/G3QHZcky/image.png)

DevOps 与 SRE 实战涵盖了笔者对于大型软件系统开发与运维工程中的偏交付、运维向的知识沉淀。DevOps 的出现，运维的身份职责发生了转变，它不再是专门跑任务脚本或者与机器打交道的人，而是变成了 OpenStack 或者 Kubernetes 的专家，通过搭建/管理相关的分布式集群，为研发提供可靠的应用运行环境。DevOps 更重要的方面还是改变了应用交付的流程，从传统的搭火车模式走向持续交付，应用的架构和形态改变了，其方法论也随之而改变。DevOps 和持续交付也被认为是云原生应用的要素。至于 AIOps 是 DevOps 在实践 AI 过程中的一些应用，称不上是范式的改变，AI 在运维领域还远远取代不了人的作用。

> 本书的精排目录导航版请参考 [https://ng-tech.icu/DevOps-Series](https://ng-tech.icu/DevOps-Series)。

## 背景分析

分布式架构解决了互联网应用吞吐量的瓶颈；越来越成熟的分布式中间件也屏蔽了分布式系统的复杂度，提升了开发工程师的工作效率；自动化运维工具则提升了运维工程师的工作效率。但是，由于目标不同，在固有的将开发和运维划分为不同部门的组织结构中，部门之间的配合并不总是很默契的。开发部门的驱动力通常是频繁交付新特性，而运维部门则更关注服务的可靠性。两者目标的不匹配使得部门之间产生了鸿沟，从而降低了业务交付的速度与价值。

直到 DevOps 方法论出现，开发与运维之间的鸿沟才得以渐渐消失；通常，影响一个项目的三个因素分别是速度(时间)、可靠性和成本。开发需要有按时交付的速度，而运营需要有可靠性。DevOps 可以保证以低成本的方式实现速度和可靠性，帮助开发工程师和运维工程师在实现各自目标的前提下，向最终用户交付价值最大化、质量最高的成果的一系列基本原则。DevOps 在软件开发和交付流程中强调“在产品管理、软件开发以及运维之间进行沟通与协作”。DevOps 是一种使持续交付成为可能的理念，关注于所有人共同协作以改进开发效率方面的衡量(比如生产力)，同时增加稳定性并降低平均故障修复时间。

DevOps 是一种公司文化的变迁，它代表了开发、运维和测试等环节之间的协作，因此多种工具可以组成一个完整的 DevOps 工具链。Chef 的创始人 Adam Jacob 将 DevOps 定义为一种文化和专业的运动。

![](https://i.postimg.cc/wvLsRT8N/image.png)

DevOps 会涉及到各种模式，包括：持续改进、组织文化、学习曲线、持续交付、持续学习、持续协作和自动化：

- 价值流，它指一个组织针对客户的需求所执行的各项交付活动的顺序。也就是指你如何把一个想法最终变现的过程。

- 交付时间，它指价值流从开始到结束，全程转化的耗时。一般情况下，交付时间是指呈现到客户眼前所花费的时间。

- 周期时间，它始于按照需求所开展的工作，终于准备好交付项目的时候。

- 交付时间的掌控能力，意味着我们对 DevOps 的运用水平。

- 部署交付时间，反映了我们在自动化方面的水平。

由此可见，组织应遵循 DevOps 的模式和实践方式，以减少交付的时间。他们完全可以从中选取诸如：放大反馈或加强持续学习文化等一个或多个适合自身的 DevOps 方法。GitOps 被认为是下一代的 DevOps，让运维工作变得与写代码的方式一样，将 Git 仓库作为运维工作的“the single source of truth”，这对于多云、混合云和多集群部署是非常有价值的。Git 所具备的版本管理能力让运维工作变得更加可溯与可控。总的说来，易用性解决的是软件开发效率、工程质量和人力成本问题。

# Nav | 导读

![思维脑图](https://i.postimg.cc/52VkSTkK/DevOPS.png)

- 如果您想搭建 APM 监控体系，那么建议阅读[监控体系](./监控体系)系列章节。

# About | 关于

<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<!-- ACKNOWLEDGEMENTS -->

## Acknowledgements

- [Awesome-Lists](https://github.com/wx-chevalier/Awesome-Lists): 📚 Guide to Galaxy, curated, worthy and up-to-date links/reading list for ITCS-Coding/Algorithm/SoftwareArchitecture/AI. 💫 ITCS-编程/算法/软件架构/人工智能等领域的文章/书籍/资料/项目链接精选。

- [Awesome-CS-Books](https://github.com/wx-chevalier/Awesome-CS-Books): :books: Awesome CS Books/Series(.pdf by git lfs) Warehouse for Geeks, ProgrammingLanguage, SoftwareEngineering, Web, AI, ServerSideApplication, Infrastructure, FE etc. :dizzy: 优秀计算机科学与技术领域相关的书籍归档。

## Copyright & More | 延伸阅读

笔者所有文章遵循[知识共享 署名 - 非商业性使用 - 禁止演绎 4.0 国际许可协议](https://creativecommons.org/licenses/by-nc-nd/4.0/deed.zh)，欢迎转载，尊重版权。如果觉得本系列对你有所帮助，欢迎给我家布丁买点狗粮(支付宝扫码)~

[![技术视野](https://s2.ax1x.com/2019/12/03/QQJLvt.png)](https://github.com/wx-chevalier/Awesome-MindMaps)

您还可以前往 [NGTE Books](https://ng-tech.icu/books/) 主页浏览包含知识体系、编程语言、软件工程、模式与架构、Web 与大前端、服务端开发实践与工程架构、分布式基础架构、人工智能与深度学习、产品运营与创业等多类目的书籍列表：

[![NGTE Books](https://s2.ax1x.com/2020/01/18/19uXtI.png)](https://ng-tech.icu/books/)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/wx-chevalier/DevOps-Series.svg?style=flat-square
[contributors-url]: https://github.com/wx-chevalier/DevOps-Series/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/wx-chevalier/DevOps-Series.svg?style=flat-square
[forks-url]: https://github.com/wx-chevalier/DevOps-Series/network/members
[stars-shield]: https://img.shields.io/github/stars/wx-chevalier/DevOps-Series.svg?style=flat-square
[stars-url]: https://github.com/wx-chevalier/DevOps-Series/stargazers
[issues-shield]: https://img.shields.io/github/issues/wx-chevalier/DevOps-Series.svg?style=flat-square
[issues-url]: https://github.com/wx-chevalier/DevOps-Series/issues
[license-shield]: https://img.shields.io/github/license/wx-chevalier/DevOps-Series.svg?style=flat-square
[license-url]: https://github.com/wx-chevalier/DevOps-Series/blob/master/LICENSE.txt
