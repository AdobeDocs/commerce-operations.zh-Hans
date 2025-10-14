---
title: Adobe Commerce上的托管警报： [!DNL Redis] 内存严重警报
description: 本文提供了在 [!DNL Redis] 中收到Adobe Commerce的 [!DNL New Relic]内存严重警报时的故障排除步骤。 需要立即采取措施来解决问题。
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
exl-id: 1233889e-8c02-4ad6-b12c-683010b7bf35
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# Adobe Commerce上的托管警报： [!DNL Redis]内存严重警报

本文提供当您在[!DNL Redis]中收到Adobe Commerce的[!DNL New Relic]内存严重警报时的故障排除步骤。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。

![new_relic_redis_memory_critical.png](../../assets/managed-alerts/new_relic_redis_memory_critical.png)

## 受影响的产品和版本

云基础架构上所有版本的Adobe Commerce Pro规划架构

## 问题

如果您已为Adobe Commerce[!DNL New Relic]注册了[托管警报，并且一个或多个警报阈值已超出，则将在](managed-alerts-for-magento-commerce.md)中收到警报。 这些警报由Adobe开发，用于通过支持和工程部门的分析为商家提供一组标准警报。

**<u>做！</u>**

* 中止任何计划的部署，直到清除此警报。
* 如果您的网站处于或完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅《Commerce安装指南》中的[启用或禁用维护模式](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅《Commerce安装指南》中的[维护免除IP地址列表](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。

**<u>不要！</u>**

* 启动其他营销活动，这可能会给您的网站带来其他页面查看次数。
* 运行索引器或其他cron，这可能会在CPU或磁盘上造成额外的压力。
* 执行任何主要管理任务(即Commerce管理员中的主要操作，例如数据导入/导出、刷新媒体、保存具有大量已分配产品的类别以及批量更新)。
* 清除缓存。

## 解决方案

按照以下步骤确定原因并排除故障。

**由于这是一个严重警报，强烈建议您在尝试解决问题之前完成步骤1（从步骤2开始）。**

1. 检查Adobe Commerce支持票证是否存在。 有关步骤，请参阅Commerce支持知识库中的[跟踪您的支持工单](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case)。 支持人员可能已经收到[!DNL New Relic]阈值警报，已创建票证并开始处理此问题。 如果不存在票证，请创建一个。 票证应包含以下信息：

   * 联系原因：选择&#x200B;**[!UICONTROL New Relic CRITICAL alert received]**。
   * 警报的说明。
   * [[!DNL New Relic] 事件链接](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/)。 这包含在您的[Adobe Commerce托管警报](managed-alerts-for-magento-commerce.md)中。

1. 如果不存在支持票证，请转到[!DNL Redis]one.newrelic.com[&#x200B; > &#x200B;](https://login.newrelic.com) > **[!UICONTROL Infrastructure]**&#x200B;页面检查&#x200B;**[!UICONTROL Third-party services]**&#x200B;已用内存是否正在增加或减少，然后选择[!DNL Redis]仪表板。 如果它稳定或增大，请[提交支持票证](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)以升级群集，或将`maxmemory`限制提高到下一级别。
1. 如果您无法确定[!DNL Redis]内存消耗增加的原因，请查看近期趋势以确定近期代码部署或配置更改（例如，新客户组和目录的大幅更改）中存在的问题。 建议您查看过去七天的活动，以了解代码部署或更改中的任何关联。
1. 检查第三方扩展是否存在行为不端：

   * 请尝试查找与最近安装的第三方扩展以及问题开始时间的关联。
   * 查看可能影响Adobe Commerce缓存并导致缓存快速增长的扩展。 例如，自定义布局块、覆盖缓存功能以及在缓存中存储大量数据。

1. 如果没有证据表明扩展行为不正确，请[安装最新修补程序以修复Adobe Commerce在云基础架构上的 [!DNL Redis] 问题](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues)。
1. 如果上述步骤不能帮助您识别或排除问题的根源，请考虑启用L2缓存以减少应用程序与[!DNL Redis]之间的网络流量。 有关什么是L2缓存的一般信息，请参阅《Commerce配置指南》中的[Adobe Commerce应用程序中的L2缓存](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/cache/level-two-cache)。 要为云基础架构启用二级缓存，请尝试以下操作：

   * 如果版本低于2002.1.2，请升级ECE工具。
   * 使用[使用REDIS\_BACKEND变量](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend)并更新`.magento.env.yaml`文件来配置二级缓存：

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
