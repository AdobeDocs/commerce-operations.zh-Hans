---
title: “如何使用 [!DNL Observation for Adobe Commerce] nerdlet”
description: 了解如何使用 [!DNL Observation for Adobe Commerce] 内德莱特。
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 如何使用 [!DNL Observation for Adobe Commerce] 内尔特

## 一般的问题处理方法

检查环境资源状态：

* 检查% **[!UICONTROL Storage Free and MySQL % free storage by node]** 框架。

   * 如果看到存储空间不足，请按照框架标题中的链接操作。

* 检查% **[!UICONTROL free system memory and Swap memory free in bytes]** 框架。

   * 如果这些显示的内存非常低，则它们可能会导致问题。

* 检查 **[!UICONTROL Alerts during the timeframe]** 框架。

   * 云基础架构提供的Adobe Commerce [!DNL Managed alerts]. 您可以单击标题中的链接以查看 [!DNL Support Knowledge Base] 可帮助确定您对特定警报的操作的文章。

* 检查 **[!UICONTROL CPU % by host]** 框架：如果CPU利用率很高，请检查 [!DNL Support Knowledge Base] 框架标题中的文章。 此外，检查以确保数据库导入/导出或备份在流量高峰期不执行。

* 检查 **[!UICONTROL Web Traffic volume compared to one week ago]** 框架：如果同一时段的流量比前一周高得多，是否可以解释（例如销售活动或已营销的新产品）？
   * 如果流量增长无法解释，请查看生产环境的平均响应时间（毫秒）。 导致响应时间的较高流量是否与正常流量不同？ 展开时间范围以查看它是否是异常。
   * 流量的增加是否会影响Web交易？ 检查 **[!UICONTROL Response Code]** 错误的框架。 如果网站关闭，您可以单击 `Site Down?` 链接。 该帧将识别发生的任何错误及其频度。
   * 有人对您的网站进行了更改吗？ 的 **[!UICONTROL Deployment Log Entries]** 框架将指示在问题时间范围内是否进行了任何部署。 如果问题在部署后立即出现，则可能是部署活动正在向站点添加额外的负载（缓存清除、服务重新启动等）。
   * 是否发生了大小调整或大小调整？ 如果您的网站已临时调整大小，则可能已返回到其原始群集大小。 如果请求增加站点容量，则可能会发生更大。 检查 **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** 框架。 此帧有时会检测到某个特定节点发生中断。 如果看到大小减小，则可能表示一个或多个节点出现问题。

* 的 **[!UICONTROL IP Frequency]** 选项卡标识针对源服务器发出的IP地址的请求频率(这意味着无法从 [!DNL Fastly] 从74开始，没有缓存)。

   * 对于任意 [!DNL Fastly] 相关问题，请检查 **[!UICONTROL Fastly Cache]** 框，然后选择“错误”方面以查看错误请求的百分比。 如果后端问题与非Web加载相一致，则它们可能会指示后端问题。
   * 如果加载似乎不是由于Web流量所致，则可能会出现错误或生成非Web请求，如慢速查询或 [!DNL crons].

* 检查 **[!UICONTROL Database Errors]** 与问题/问题时间轴一致的错误的帧。
* 检查 **[!UICONTROL Database mysql-slow.log]** 用于标识正在发生的SQL语句的框架。 `INSERT`, `UPDATE`和 `DELETE` 如果查询未优化，则可能需要一些时间。 均等 `SELECT` 如果对大型表执行语句，则会非常低效。
* **[!UICONTROL PHP States]** 和 **[!UICONTROL PHP Errors]** 帧将显示PHP的潜在问题。 的 **[!UICONTROL PHP States]** 帧将显示PHP进程终止、开始和服务到达节点就绪状态时。 的 **[!UICONTROL PHP Errors]** frame可能有助于隔离PHP问题所在的位置，如内存大小、工作程序或服务器数量。
* 为了查看事务中的延迟，可以按列对“事务 — 平均、最大、最小”表进行排序，以显示运行最长的事务持续时间。 过载的集群将在事务中具有潜在的持续时间，但它也会显示异常，这些异常可能会用方法或 [!DNL cron].
* 的 **[!UICONTROL Cron error]** 帧将显示 [!DNL cron] 锁定，可能与 [!DNL cron] 日志和共享暂存 [!DNL crons] 当存在专用暂存环境时可能在生产环境中运行的暂存环境。
* 的 [!UICONTROL ElasticSearch Errors] 框显示可能表示 [!DNL Elasticsearch] 查询、数据或索引。
