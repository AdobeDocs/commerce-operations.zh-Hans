---
title: 在Adobe Commerce上管理警报：MariaDB警报
description: 本文提供了在 [!DNL New Relic]中收到Adobe Commerce的MariaDB警报时的故障排除步骤。 MariaDB警报监控高查询负载以及过度的数据操作语言(DML)查询。 两者都可能导致用户体验降低甚至停机。 您可以接收两种警报。
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# 在Adobe Commerce上管理警报：MariaDB警报

本文提供了在[!DNL New Relic]中收到Adobe Commerce的MariaDB警报时的故障排除步骤。 MariaDB警报监控高查询负载以及过度的数据操作语言(DML)查询。 两者都可能导致用户体验降低甚至停机。 您可以接收两种警报：

* DML查询警告
* DML查询关键

## 受影响的产品和版本

Adobe Commerce on cloud infrastructure Pro计划架构

## 问题

如果您已为Adobe Commerce[!DNL New Relic]注册了[个托管警报，并且一个或多个警报阈值已超出，则您将在](managed-alerts-for-magento-commerce.md)中收到托管警报。 这些警报由Adobe开发，旨在通过支持和工程部门的分析为客户提供一组标准。

**做！**

* 中止任何计划的部署，直到清除此警报。
* 如果您的网站处于或完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅《Commerce安装指南》中的[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅[维护免除IP地址列表](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。
* 结束任何脚本，例如导入，如果网站性能受到影响，则这些脚本可能会导致警报。

**不要！**

* 运行索引器或其他cron，这可能会对MariaDB造成额外压力。
* 执行任何主要管理任务(即Commerce管理、数据导入/导出)。
* 清除缓存。

## 解决方案

**DML查询(使用UPDATE、INSERT和DELETE修改数据库的查询)**

如果您收到“DML查询严重”警报，请从步骤1开始。 如果您收到“DML查询警告”警报，请从第二步开始。

1. 检查Adobe Commerce支持票证是否存在。 有关步骤，请参阅我们的知识库[跟踪您的支持工单](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case)。 支持人员可能已收到[!DNL New Relic]阈值警报，已创建票证并开始处理此问题。 如果不存在票证，请创建一个。 票证应包含以下信息：
   * 联系原因：选择&#x200B;**[!UICONTROL New Relic MariaDB alert received]**。
   * 警报的说明。
   * [[!DNL New Relic] 事件链接](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 这包含在您的[Adobe Commerce托管警报](managed-alerts-for-magento-commerce.md)中。
1. 要确定问题的来源，请尝试识别DML查询：
   1. 使用New Relic [数据库页](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)中的步骤检查数据库操作。
   1. 按&#x200B;**[!UICONTROL CALL COUNT]**&#x200B;排序，然后按&#x200B;**[!UICONTROL OPERATION]**。 审核`INSERT`、`DELETE`和`UPDATE`操作。
   1. 寻找高平均。
   1. 单击直达以查找数据库操作调用方。 这将按时间标识使用该查询的事务。
   1. 寻找代码优化或操作优化：
      * 代码优化：寻求通过批量插入/更新、最大程度地减少索引使用或限制代码来优化查询。
      * 操作优化：卸载资源密集型数据修改以缩短通信时间。
      * 其他优化：确保您使用的是最新版本的ECE-Tools。 有关步骤，请参阅Commerce on Cloud指南中的[更新ece-tools版本](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)。
