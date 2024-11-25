---
title: 优化后端性能
description: 了解如何优化Adobe Commerce网站的后端性能。
badge: label="由objectsource提供" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---

# 优化后端性能的最佳实践

本主题概述了调查和优化Adobe Commerce网站后端性能的最佳实践，重点是数据库优化和测试。 开发人员可以使用此信息来调查每个Commerce项目的独特上下文，并发现优化后端配置和操作以提高站点性能的机会。

>[!NOTE]
>
>Recommendations和示例是受objectsource在真实客户端参与中遵循的流程启发而来的，这些流程旨在大规模提供高性能Adobe Commerce站点。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 优化数据库以提高性能

数据库优化是增强用户体验和增加销售的一种有效方法。 优化数据库(Commerce站点的骨干)时，您可以防止网站性能变慢并消除给客户带来摩擦的冗长加载时间。

### 压力测试

高流量时期（如黑色星期五）要求Commerce站点处理大量流量。 为准备此类事件，压力测试对于了解网站如何在指数级负载增长的情况下运行至关重要。

可用于压力测试的工具之一是GTmetrix。 通过配置GTmetrix来复制和乘以正常的访客行为和操作，量规站点负载准备情况会增加。 然后，运行测试以识别并解决在主要购物事件期间可能影响性能和网站可用性的问题。

详细了解如何为高流量时期准备Commerce项目：

- [假日准备工作](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [假日购物分析](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [激增容量增加](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### 负载测试

您还可以使用GTmetrix或类似的工具来负载测试Commerce项目。 作为压力测试的前驱，负载测试对于大规模、高流量的站点是必不可少的。 通过预测并解决在峰值负载下影响站点性能的问题，防止意外站点中断、客户受挫和经济损失。

使用GTmetrix模拟高流量并分析站点性能，以获取有关站点容量的明确信息。 此分析有助于发现并解决瓶颈问题，同时发现优化机会，从而确保Commerce站点能够在负载增加的情况下有效运行。

了解有关测试Adobe Commerce项目的更多信息：

- [测试指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html) （云基础架构）
- [应用程序测试](https://developer.adobe.com/commerce/testing/guide/)

### 识别并解决性能问题

通过使用New Relic和Observation for Adobe Commerce等各种工具来检测瓶颈并有效优化Commerce站点，从而解决性能问题。 云基础架构上的Adobe Commerce中包括[New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)，云和内部部署中包括Adobe Commerce的[观察](/help/tools/observation-for-adobe-commerce/intro.md)。

使用这些工具分析网站性能并识别与以下内容相关的性能问题：

- CPU密集型功能
- 查询和后端操作的缓存管理配置
- 第三方API调用
- Cron计划

例如，您可以仔细检查交易，重点关注产品详细信息和类别页面。 确定可优化以提高性能的耗时流程。 在一次客户端参与中，objectsource注意到产品详细信息页面上存在性能问题，并发现一个API调用占用的性能时间的3.5%。 他们基于此结果检查了代码执行的层次结构，以查明和修复导致瓶颈的问题。

了解有关管理站点性能的更多信息：

- [性能监控](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) （云基础架构）
- [配置最佳实践](/help/performance/configuration.md)
- [Adobe Commerce观察](/help/tools/observation-for-adobe-commerce/intro.md)

### 优化MySQL性能

通过实施数据库群集和查询优化来解决MySQL性能问题是在高流量时段（如“黑色星期五”）之前和期间提高性能的有效方法。

#### 实施数据库群集

高流量网站经常面临数据库瓶颈，主要原因是依赖单个MySQL服务器。 通过实施数据库群集，您可以解决这些瓶颈问题。数据库群集是一种分布式体系结构，可提高性能并确保高可用性。

通过使多个Web节点连接到多个MySQL服务器，数据库群集最大程度地减少了与数据库相关问题在流量高峰期的影响。 使用Galera Cluster等工具为Commerce站点设置数据库群集。 Galera群集包含在云基础架构](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html)上部署的[Adobe Commerce项目中。

#### 优化MySQL查询

通常，大多数Adobe Commerce站点的基础架构包含连接到单个MySQL服务器的多个Web节点。

在此设置中，每个前端Web节点都连接到Galera群集，该群集允许多个MySQL服务器。 增加前端Web节点数量可以提高应用程序性能，但单个MySQL服务器仍然是一个瓶颈。

为了优化MySQL服务器性能并最大限度地减少瓶颈，必须识别并减少不必要的查询。 例如，如果您每秒发送1,000个查询，但只需200个，则优化并减少查询计数可以显着提升性能。

了解有关配置和优化MySQL的详细信息：

- [数据库配置的最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- Galera DB复制的[复制缓慢](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [一般MySQL准则](/help/installation/prerequisites/database/mysql.md)
- [MySQL查询缓存](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## 有效地管理cron作业：性能和时间

Cron作业在处理站点后台任务（如报告生成和产品索引）时起着至关重要的作用。 但是，cron作业优化需要仔细考虑它们对整体性能的影响。 开发人员必须评估调度频率，并根据特定需求确定最佳计时。

为了平衡性能和便利性，通常建议在低流量期间安排cron作业。 然而，与不同时区的客户打交道可能会带来挑战，需要以深思熟虑的方式确保跨多个地区的和谐体验。

如果您负责优化cron性能和时间，请查看Commerce管理员的当前cron配置，并了解如何为Commerce项目设置和配置cron作业。

此外，您还可以使用针对Adobe Commerce的观察来查看与cron相关的绩效指标。 此工具将来自多个来源的日志数据整合在一起，以帮助您更好地管理Adobe Commerce站点性能和诊断问题。

了解有关Adobe Commerce cron实施的更多信息：

- _Commerce Admin Systems用户指南_&#x200B;中的[Cron（计划任务）](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html)
- [应用程序配置 — crons属性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) （云基础架构）
- [配置并运行crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)（本地）
- Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)的[观察结果（请参阅[!UICONTROL Cron]和[!UICONTROL MySQL]选项卡。）
