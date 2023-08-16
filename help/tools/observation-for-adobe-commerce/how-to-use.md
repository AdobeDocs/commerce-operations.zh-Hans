---
title: 如何使用 [!DNL Observation for Adobe Commerce] Nerdlet
description: 了解如何使用 [!DNL Observation for Adobe Commerce] 书呆子。
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# 如何使用 [!DNL Observation for Adobe Commerce] Nerdlet

## 看问题的一般方法

检查环境资源状态：

* 检查% **[!UICONTROL Storage Free and MySQL % free storage by node]** 帧。

   * 如果存储空间不足，请按照框架标题中的链接进行操作。

* 检查% **[!UICONTROL free system memory and Swap memory free in bytes]** 帧。

   * 如果显示的内存状态非常低，则可能是问题的促成因素。

* 检查 **[!UICONTROL Alerts during the timeframe]** 框架。

   * 云基础架构上的Adobe Commerce提供 [!DNL Managed alerts]. 您可以单击标题中的链接以查看 [!DNL Support Knowledge Base] 帮助确定您对特定警报执行的操作的文章。

* 检查 **[!UICONTROL CPU % by host]** 帧：如果它的CPU利用率很高，请检查 [!DNL Support Knowledge Base] 文章在框架的标题中。 另外，检查以确保在流量高峰期不执行数据库导入/导出或备份。

* 查看 **[!UICONTROL Web Traffic volume compared to one week ago]** 框架：如果同一期间的流量比前一周高得多，能否解释一下原因（例如，促销活动或已经营销的新产品）？
   * 如果无法解释流量增加，请查看生产环境的平均响应时间（毫秒）。 对响应时间贡献较大的流量是否与正常情况不同？ 展开时间范围以查看它是否为异常。
   * 流量的增加是否会影响Web交易？ 查看 **[!UICONTROL Response Code]** 错误框架。 如果站点已关闭，您可以单击 `Site Down?` 帧标题中的链接。 该帧将识别正在发生的任何错误及其频率。
   * 是否有人将更改部署到您的网站？ 此 **[!UICONTROL Deployment Log Entries]** 框架将指示在问题时间范围内是否进行了任何部署。 如果问题在部署后立即出现，则可能是部署活动向站点添加了额外的负载（缓存被清除、服务重新启动等）。
   * 是否发生放大或缩小操作？ 如果您的站点是临时升级的，则它可能已恢复到其原始群集大小。 如果提出增加站点容量的请求，则可能会发生扩展。 查看 **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** 框架。 此帧有时会检测到某个特定节点上的中断。 如果看到大小减少，则可能表示一个或多个节点存在问题。

* 此 **[!UICONTROL IP Frequency]** 选项卡标识来自对源服务器发出的IP地址的请求频率（这意味着无法从为请求提供服务） [!DNL Fastly] 因为没有缓存74)。

   * 对于任何 [!DNL Fastly] 相关问题，请查看 **[!UICONTROL Fastly Cache]** 框中，然后选择错误方面以查看错误的请求百分比。 如果它们与非Web加载同时发生，则可能会指示后端问题。
   * 如果加载似乎不是由Web流量引起的，则可能存在错误或非Web请求的栈积，例如查询速度缓慢或 [!DNL crons].

* 查看 **[!UICONTROL Database Errors]** 可能与问题/问题时间线一致的错误帧。
* 查看 **[!UICONTROL Database mysql-slow.log]** 用于标识正在发生的SQL语句的框架。 `INSERT`， `UPDATE`、和 `DELETE` 如果查询未优化，则命令可能需要一些时间。 平衡 `SELECT` 如果对大型表执行语句，则语句可能会非常低效。
* **[!UICONTROL PHP States]** 和 **[!UICONTROL PHP Errors]** 框架将显示PHP的潜在问题。 此 **[!UICONTROL PHP States]** 框架将显示PHP进程终止、启动以及服务通过节点到达就绪状态时。 此 **[!UICONTROL PHP Errors]** 框架可帮助确定PHP出现问题的位置，如内存大小、工作程序或服务器数量。
* 要查看事务中的延迟，可以按列对事务 — 平均、最大、最小表进行排序，以显示运行时间最长的事务持续时间。 超载的群集在事务中会有潜在的持续时间，但它也会显示异常，这些异常可能会查明方法或的问题。 [!DNL cron].
* 此 **[!UICONTROL Cron error]** 框架将显示 [!DNL cron] 锁，可能关联的SQL错误 [!DNL cron] 日志和共享暂存 [!DNL crons] 当存在专用的暂存环境时，这些环境可能正在生产环境中运行。
* 此 [!UICONTROL ElasticSearch Errors] 框架显示可能表示存在重大问题的错误 [!DNL Elasticsearch] 查询、数据或索引。
