---
title: Adobe Commerce托管警报：内存警告警报
description: 本文提供了当您在 [!DNL New Relic]中收到Adobe Commerce的内存警告警报时的故障排除步骤。 需要立即采取措施来解决问题。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 54cb28acd9e930cc915f2ab1bf04cfc61d08663c
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Adobe Commerce托管警报：内存警告警报

本文提供了在[!DNL New Relic]中收到Adobe Commerce的内存警告警报时的故障排除步骤。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。

![内存警告](../../assets/managed-alerts/memory-warning-magento-managed.png){width="500"}

## 受影响的产品和版本

Adobe Commerce on cloud infrastructure Pro计划架构

## 问题

如果您已为Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)注册了托管警报，并且一个或多个警报阈值已超出，则将在[!DNL New Relic]中收到警报。 这些警报由Adobe Commerce开发，旨在通过支持和工程部门的分析为客户提供一组标准。

<u>**做！**</u>：

* 建议在清除此警报之前，中止任何计划的部署。
* 如果您的网站处于或完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅《Commerce安装指南》中的[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅《Commerce安装指南》中的[维护免除IP地址列表](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。

<u>**不要！**</u>：

* 启动其他营销活动，这可能会给您的网站带来其他页面查看次数。
* 运行索引器或其他cron，这可能会在CPU或磁盘上造成额外的压力。
* 执行任何主要管理任务（即管理员、数据导入/导出）。
* 清除缓存。

## 解决方案

按照以下步骤确定原因并排除故障。

1. 使用[[!DNL New Relic] APM的“基础结构”页](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)识别最占用内存的进程。 有关步骤，请参阅[[!DNL New Relic] [基础结构监视主机页面： [!UICONTROL Processes]选项卡]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)。 如果像[!DNL Redis]或MySQL这样的服务是内存消耗的最大来源，请尝试以下操作：

   * 检查您是否使用最新版本。 较新版本有时可以修复内存泄漏。 如果您不是最新版本，请考虑升级。 有关步骤，请参阅Commerce on Cloud指南中的[更改服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。
   * 如果您仍然无法识别内存消耗增加的来源，请检查MySQL问题，例如长时间运行的查询、未定义主键以及重复的索引。 有关步骤，请参阅Adobe Commerce实施行动手册中的[Commerce上最常见的数据库问题](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)。
   * 如果没有MySQL问题，请检查PHP问题。 通过在CLI/终端中运行`ps aufx`来查看正在运行的进程。 在终端输出中，您将看到当前正在执行的cron作业和进程。 检查进程执行时间的输出。 如果存在执行时间较长的cron，则该cron可能会挂起。 有关疑难解答步骤，请参阅Commerce支持知识库中的[性能缓慢、运行缓慢且长时间的cron](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons)和[Cron作业卡在“正在运行”状态](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status)。

1. 如果您仍在努力找出问题的根源，请使用[[!DNL New Relic] APM的“事务”页](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)来识别具有性能问题的事务：

   * 按升序[!DNL Apdex]分数对事务排序。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)指用户对Web应用程序和服务的响应时间的满意度。 [低 [!DNL Apdex] 分](managed-alerts-for-magento-commerce-apdex-warning-alert.md)可能表示瓶颈（响应时间较长的事务）。 通常为数据库[!DNL Redis]或PHP。 有关步骤，请参阅New Relic [查看满意度最高 [!DNL Apdex] 的事务](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)。
   * 按最高吞吐量、最慢的平均响应时间、最耗时的阈值和其他阈值对事务进行排序。 有关步骤，请参阅[[!DNL New Relic] 查找具体性能问题](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。 如果您仍在努力识别问题，请使用[[!DNL New Relic] APM的基础结构页面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)。

1. 如果您无法确定内存消耗增加的原因，请查看近期趋势以确定近期代码部署或配置更改（例如，新客户组和目录的大幅更改）中存在的问题。 建议您查看过去七天的活动，以了解代码部署或更改中的任何关联。

1. 如果上述方法不能帮助您在合理的时间内找到原因和/或解决方案，请请求升级站点，或者将站点置于维护模式（如果尚未这样做）。 有关步骤，请参阅Commerce支持知识库中的[如何请求临时调整大小](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize)以及《Commerce安装指南》中的[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。

1. 如果升级使站点恢复正常运营，请考虑请求永久升级(联系您的Adobe客户团队)，或尝试通过运行负载测试和优化查询或在专用暂存中重现问题，或运行降低服务压力的代码。 请参阅Commerce on Cloud指南中的[负载和压力测试](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing)。
