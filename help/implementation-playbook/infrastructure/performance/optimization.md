---
title: 性能优化
description: 了解有关性能优化以及检查Adobe Commerce实施性能所需执行的步骤的所有信息。
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 性能优化

表现是一个大话题。 当用户遇到网站缓慢或无响应时，它会影响转化。 我们建议按照以下步骤来优化您的Adobe Commerce在云基础架构实施方面的性能：

- 评估问题
- 衡量绩效
- 确定系统中对性能改进至关重要的部分
- 修改系统部分以消除瓶颈
- 在修改后测量性能
- 如果更好，则采用或恢复

## 典型性能问题

慢速体验的影响通常由两个指标来定义，每个因素都可能因为大量原因而引起。

高时间到第一字节(TTFB)通常被视为定义服务器响应速度的指示器。 时间不仅来自处理请求的源代码执行，而且还可能会受到以下因素的影响：

- DNS查找
- 从数据库层查询速度缓慢
- 每个应用层的CPU时间
- 内存限制
- I/O等待可能会从文件读写中影响，通过套接字连接服务
- 软件设置(nginx、PHP、MySQL、Redis、Quest)
- 网络带宽
- 缓存错误
- 错误代码
- 错误的集成方法
- 慢速第三方服务响应的依赖性
- 无可扩展性的架构

慢速加载资源通常被视为定义静态资源（CSS、JavaScript、图像、视频、第三方Ajax调用响应）的指示器。

Adobe Commerce可以通过其功能扩展您的业务：

![显示Adobe Commerce可扩展功能的图表](../../../assets/playbooks/scalable-capabilities.svg)

商业规模的驱动因素也是关键因素，这也影响了整体业绩。

- 复杂和大型产品目录
- 大量管理员
- 全球店面
- 高变量流量
- 扩展接触点
- 大量交易

对于为规模而构建的分层且可缓存的体系结构，您可以使用此图作为参考。

![显示如何在可缓存架构中使用Adobe Commerce GraphQL API的图表](../../../assets/playbooks/cacheable-architecture.svg)
