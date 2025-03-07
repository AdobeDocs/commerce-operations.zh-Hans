---
title: Adobe Commerce的受管警报
description: 如果您是Adobe Commerce on cloud infrastructure Pro规划架构客户，则可以使用受管警报了解站点的运行状况。 如果您是Adobe Commerce on cloud infrastructure Starter plan架构客户，则仅会收到 [!DNL Apdex] 和错误率条件的警报。
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: efb58b920a9b72ac96bbd28aaae6210ede84e24f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Adobe Commerce的受管警报


我们设置了关键仪表板和警报，帮助您了解您的站点何时达到关键存储和[!DNL Apdex]级别（用户对应用程序和服务响应时间的满意度）。 这有助于您在发现响应时间缓慢或中断之前采取行动。 您将能够使用下面列出的文章对警报进行故障排除。 在使用警报之前，请先设置通知渠道。 请参阅Commerce on Cloud指南中的[[!DNL New Relic] 配置通知渠道](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service)。

>[!NOTE]
>
>如果Adobe Commerce警报策略的托管警报不可用，可能是由于新创建的此帐户或最近配置了[!DNL New Relic]。 在每个星期二运行一个进程，将警报策略添加到这些帐户。 警报策略应在下一个进程运行后的第二天可供您使用。 如果策略仍然缺失，请[提交Adobe Commerce支持请求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)并包含您的项目ID。

请参阅下表中的链接，这些链接指向提供这些警报的故障诊断步骤的知识库文章：

* Adobe Commerce的受管警报： CPU警告警报
* Adobe Commerce的受管警报：CPU严重警报
* Adobe Commerce托管警报：内存警告警报
* Adobe Commerce的受管警报：内存严重警报
* Adobe Commerce的托管警报： [!DNL Apdex]警告警报
* Adobe Commerce的受管警报： [!DNL Apdex]严重警报
* Adobe Commerce托管警报：磁盘警告警报
* Adobe Commerce的受管警报：磁盘严重警报
* 在Adobe Commerce上管理警报：MariaDB警报
* Adobe Commerce上的托管警报： [!DNL Redis]内存警告警报
* Adobe Commerce上的托管警报： [!DNL Redis]内存严重警报

>[!NOTE]
>
>“警告警报”和“严重警报”的设置阈值基于我们正在使用客户群的历史性能数据进行的研究结果，它代表了Adobe Commerce支持和工程团队的最新见解。 请注意，根据最新的持续分析，这些阈值可能会发生更改。 典型的警报流程是接收警报的严重性从低到高。 因此，在收到“严重”警报之前，您可能会收到“警告”警报。 有关疑难解答步骤，请参阅文章链接。

| 严重程度 | CPU | 内存 | 磁盘 | [!DNL Apdex] | MariaDB | [!DNL Redis]内存 | 疑难解答文章 |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| 警告 | ✅ |        |      |       |         |              | [Adobe Commerce托管警报： CPU警告警报](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| 关键 | ✅ |        |      |       |         |              | [Adobe Commerce的托管警报： CPU严重警报](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| 警告 |     | ✅ |      |       |         |              | [Adobe Commerce托管警报：内存警告警报](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| 关键 |     | ✅ |      |       |         |              | [Adobe Commerce的托管警报：内存严重警报](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| 警告 |     |        |      | ✅ |         |              | [Adobe Commerce的托管警报： [!DNL Apdex] 警告警报](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| 关键 |     |        |      | ✅ |         |              | [Adobe Commerce的托管警报： [!DNL Apdex] 严重警报](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| 警告 |     |        | ✅ |       |         |              | [Adobe Commerce的托管警报：磁盘警告警报](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| 关键 |     |        | ✅ |       |         |              | [Adobe Commerce的托管警报：磁盘严重警报](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| 警告和严重 |     |        |      |       | ✅ |              | [Adobe Commerce上的托管警报： MariaDB警报](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| 警告 |     |        |      |       |         | ✅ | [Adobe Commerce上的托管警报： [!DNL Redis] 内存警告警报](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| 关键 |     |        |      |       |         | ✅ | [Adobe Commerce上的托管警报： [!DNL Redis] 内存严重警报](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |
