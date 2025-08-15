---
title: 如何使用 [!DNL Observation for Adobe Commerce] nerdlet
description: 了解如何使用 [!DNL Observation for Adobe Commerce] nerdlet。
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# 如何使用[!DNL Observation for Adobe Commerce] Nerdlet

## 看问题的一般方法

检查环境资源状态：

* 检查&#x200B;**[!UICONTROL Storage Free and MySQL % free storage by node]**&#x200B;帧的%。

   * 如果存储空间不足，请按照框架标题中的链接进行操作。

* 检查&#x200B;**[!UICONTROL free system memory and Swap memory free in bytes]**&#x200B;帧的%。

   * 如果显示的内存状态非常低，则可能是问题的促成因素。

* 检查&#x200B;**[!UICONTROL Alerts during the timeframe]**&#x200B;帧。

   * 云基础架构上的Adobe Commerce提供[!DNL Managed alerts]。 您可以单击标题中的链接以查看[!DNL Support Knowledge Base]篇文章，这些文章有助于确定您对特定警报执行的操作。

* 检查&#x200B;**[!UICONTROL CPU % by host]**&#x200B;帧：如果它显示高的CPU利用率，请检查帧标题中的[!DNL Support Knowledge Base]文章。 另外，检查以确保在流量高峰期不执行数据库导入/导出或备份。

* 检查&#x200B;**[!UICONTROL Web Traffic volume compared to one week ago]**&#x200B;帧：如果同一期间的流量比前一周高出许多，能否解释该情况（例如，已营销的销售活动或新产品）？
   * 如果无法解释流量增加，请查看生产环境的平均响应时间（毫秒）。 对响应时间贡献较大的流量是否与正常情况不同？ 展开时间范围以查看它是否为异常。
   * 流量的增加是否会影响Web交易？ 检查&#x200B;**[!UICONTROL Response Code]**&#x200B;帧是否有错误。 如果站点已关闭，您可以单击框架标题中的`Site Down?`链接。 该帧将识别正在发生的任何错误及其频率。
   * 是否有人将更改部署到您的网站？ **[!UICONTROL Deployment Log Entries]**&#x200B;框架将指示在问题时间范围内是否完成了任何部署。 如果问题在部署后立即出现，则可能是部署活动向站点添加了额外的负载（缓存被清除、服务重新启动等）。
   * 是否发生放大或缩小操作？ 如果您的站点是临时升级的，则它可能已恢复到其原始群集大小。 如果提出增加站点容量的请求，则可能会发生扩展。 检查&#x200B;**[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**&#x200B;帧。 此帧有时会检测到某个特定节点上的中断。 如果看到大小减少，则可能表示一个或多个节点存在问题。

* **[!UICONTROL IP Frequency]**&#x200B;选项卡标识来自针对源服务器发出的IP地址的请求频率（这意味着无法从[!DNL Fastly]为该请求提供服务，因为它未缓存74）。

   * 有关任何[!DNL Fastly]相关问题，请检查&#x200B;**[!UICONTROL Fastly Cache]**&#x200B;框架，然后选择错误方面，以查看错误的请求百分比。 如果它们与非Web加载同时发生，则可能会指示后端问题。
   * 如果加载似乎不是由Web流量引起的，则可能存在错误或非Web请求的栈积，例如查询速度缓慢或[!DNL crons]。

* 检查&#x200B;**[!UICONTROL Database Errors]**&#x200B;帧中是否存在可能与问题/问题时间表一致的错误。
* 检查&#x200B;**[!UICONTROL Database mysql-slow.log]**&#x200B;帧以标识正在发生的SQL语句。 如果未优化查询，`INSERT`、`UPDATE`和`DELETE`命令可能需要一些时间。 即使是`SELECT`语句如果针对大型表执行，也可能非常低效。
* **[!UICONTROL PHP States]**&#x200B;和&#x200B;**[!UICONTROL PHP Errors]**&#x200B;帧将显示PHP的潜在问题。 **[!UICONTROL PHP States]**&#x200B;框架将显示PHP进程终止、启动以及服务按节点到达就绪状态时。 **[!UICONTROL PHP Errors]**&#x200B;框架可帮助确定PHP出现问题的位置，如内存大小、工作程序或服务器数量。
* 要查看事务中的延迟，可以按列对事务 — 平均、最大、最小表进行排序，以显示运行时间最长的事务持续时间。 过载的群集在事务中会有潜在的持续时间，但也会显示可能查明方法或[!DNL cron]问题的异常。
* 当存在专用暂存环境时，**[!UICONTROL Cron error]**&#x200B;框架将显示[!DNL cron]锁定、可能与[!DNL cron]日志关联的SQL错误以及可能在生产环境中运行的共享暂存[!DNL crons]。
* [!UICONTROL ElasticSearch Errors]框架显示错误，这些错误可能指示[!DNL Elasticsearch]查询、数据或索引存在严重问题。
