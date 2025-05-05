---
title: Adobe Commerce上的托管警报： CPU严重警报
description: 本文提供了在 [!DNL New Relic]中收到Adobe Commerce的CPU严重警报时的故障排除步骤。 需要立即采取措施来解决问题。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: b30266b8f39989103ca70fa3e57ade8cea9b0dcc
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Adobe Commerce上的托管警报： CPU严重警报

本文提供了在[!DNL New Relic]中收到Adobe Commerce的CPU严重警报时的故障排除步骤。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。

![磁盘严重警报](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## 受影响的产品和版本

Adobe Commerce on cloud infrastructure Pro计划架构

## 问题

如果您已为Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)注册了个托管警报，并且一个或多个警报阈值已超出，则您将在[!DNL New Relic]中收到托管警报。 这些警报由Adobe Commerce开发，旨在通过支持和工程部门的分析为客户提供一组标准。

<u>**做！**</u>：

* 中止任何计划的部署，直到清除此警报。
* 如果您的网站处于或完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅《Commerce安装指南》中的[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅《Commerce安装指南》中的[维护免除IP地址列表](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。

<u>**不要！**</u>：

* 启动其他营销活动，这可能会给您的网站带来其他页面查看次数。
* 运行索引器或其他cron，这可能会在CPU或磁盘上造成额外的压力。
* 执行任何主要管理任务(即Commerce管理员、数据导入/导出)。
* 清除缓存。

如果您在调查并解决警报原因之前执行了任何“不响应”操作，则您的网站可能会变得无响应（如果您尚未经历网站中断）。

## 解决方案

按照以下步骤确定原因并排除故障。

>[!WARNING]
>
>由于这是一个严重警报，强烈建议您在尝试排查问题（从步骤2开始）之前完成&#x200B;**步骤1**。

检查Adobe Commerce支持工单是否存在。 有关步骤，请参阅Commerce支持知识库中的[跟踪您的支持工单](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case)。 支持人员可能已收到[!DNL New Relic]阈值警报，创建了票证，并开始处理此问题。 如果不存在票证，请创建一个。 票证应包含以下信息：

1. 联系原因：选择&#x200B;**[!UICONTROL New Relic CRITICAL alert received]**。
1. 警报的说明。
1. [[!DNL New Relic] 事件链接](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 这包含在您的[Adobe Commerce托管警报](managed-alerts-for-magento-commerce.md)中。
1. 使用[[!DNL New Relic] APM的“事务”页](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)识别具有性能问题的事务：
   * 按升序Apdex分数对事务排序。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)指用户对Web应用程序和服务的响应时间的满意度。 [低 [!DNL Apdex] 分](managed-alerts-for-magento-commerce-apdex-warning-alert.md)可能表示瓶颈（响应时间较长的事务）。 通常，它与数据库[!DNL Redis]或PHP相关。 有关步骤，请参阅New Relic [查看满意度最高 [!DNL Apdex] 的事务](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)。
   * 按最高吞吐量、最慢的平均响应时间、最耗时的阈值和其他阈值对事务进行排序。 有关步骤，请参阅[!DNL New Relic] [查找特定的性能问题](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。
1. 如果您仍在努力识别源，请使用[[!DNL New Relic] APM的“基础架构”页](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page)来识别资源密集型服务。 有关步骤，请参阅[!DNL New Relic] [基础结构监视主机页面：进程选项卡](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)。
1. 如果标识了源，请通过SSH连接到环境以进一步调查。 有关步骤，请参阅Commerce on Cloud指南中的[SSH到您的环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)。
1. 如果你还在努力找出问题的根源：
   * 查看最近的趋势，以确定最近的代码部署或配置更改（例如，新客户组和目录的大幅更改）中存在的问题。 建议您查看过去七天的活动，以了解代码部署或更改中的任何关联。
   * 考虑检查和禁用平面目录。 有关步骤，请参阅Commerce支持知识库中的[性能缓慢、运行缓慢且长时间的crons](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons)。
   * 如果您怀疑正在遭受DDoS攻击，请尝试阻止机器人流量。 有关步骤，请参阅Commerce支持知识库中的[如何阻止Adobe Commerce在Fastly级别](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level)上的云基础架构上的恶意流量。
1. 如果问题看起来是暂时性的，请执行缓解步骤（如升级）或将站点置于维护模式。 有关步骤，请参阅Commerce支持知识库中的[如何请求临时调整大小](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize)以及《Commerce安装指南》中的[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 如果升级使站点恢复正常运营，请考虑请求永久升级(联系您的Adobe客户团队)，或尝试通过运行负载测试并优化查询或降低服务压力的代码在专用暂存中重现问题。 有关步骤，请参阅Commerce on Cloud指南中的[负载和压力测试](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing)。
