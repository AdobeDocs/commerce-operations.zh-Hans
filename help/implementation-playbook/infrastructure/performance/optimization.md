---
title: 性能优化
description: 了解有关性能优化的所有信息，以及查看Adobe Commerce实施性能时应采取的步骤。
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 性能优化

性能是一个大主题。 当用户遇到网站速度缓慢或无响应时，它会影响转化。 我们建议执行以下步骤，以优化Adobe Commerce在云基础架构实施中的性能：

- 评估问题
- 衡量绩效
- 确定提高性能的关键系统部分
- 修改部分系统以移除瓶颈
- 衡量修改后的性能
- 如果效果更好，请采用它或恢复

## 典型性能问题

慢速体验的影响通常由两个指标定义，每个因素都可能由于大量原因而产生。

高首字节时间(TTFB)通常被视为定义服务器响应速度的指标。 时间不仅来自处理请求的源代码执行，而且还可能受以下因素的影响：

- DNS查找
- 来自DB层的查询速度缓慢
- 每个应用层的CPU时间
- 内存限制
- I/O等待可能会影响文件读取和写入，通过套接字连接服务
- 软件设置(nginx、PHP、MySQL、Redis、Varnish)
- 网络带宽
- 缓存错误
- 错误代码
- 错误的集成方法
- 依赖缓慢的第三方服务响应
- 没有可扩展性的体系结构

加载缓慢的资源通常被视为定义静态资源（CSS、JavaScript、图像、视频、第三方Ajax调用响应）的指示器。

Adobe Commerce可以通过其功能随您的业务进行扩展：

![显示Adobe Commerce的可扩展功能的示意图](../../../assets/playbooks/scalable-capabilities.svg)

在商业运作中，也有一些推动规模的关键因素，这也会影响整体表现。

- 复杂而庞大的产品目录
- 大量管理员
- 全局店面
- 高变量流量
- 扩展接触点
- 大流量事务

对于针对规模而构建的分层和可缓存体系结构，您可以使用此图作为参考。

![显示如何在可缓存架构中使用Adobe Commerce GraphQL API的图表](../../../assets/playbooks/cacheable-architecture.svg)
