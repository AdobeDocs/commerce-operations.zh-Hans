---
title: “ [!DNL Infra] 选项卡”
description: 的 [!DNL Infra] tab可隔离问题和导致基础结构问题的原因。
source-git-commit: 38467ebd2ec29f9e1679182fb1ee7076d738664b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# 的 [!DNL Infra] 选项卡

的 **[!DNL Infra]** tab可隔离问题和导致基础结构问题的原因。 进一步介绍了您在选项卡上可以看到的帧。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![服务警报](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

的 **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** 图表显示由 [!DNL New Relic] 基础设施代理。 这将显示服务重新启动，其中许多与部署相关。

## [!UICONTROL Inode usage by mount]

![按装载使用索引码](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

的 **[!UICONTROL Inode usage by mount]** 帧显示 [!DNL inode] 在选定时间范围内按装入方式使用。 即使存储空间可能很大，但如果某个节点耗尽 [!DNL inodes]，则会显示缺少可用存储。 删除文件（尤其是小文件）将释放空间并创建 [!DNL inodes] 可用。

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![时间线上的vCPU层视图超过2周](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

的 **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** 此框架显示超过两周的选定时间范围内的vCPU层视图。 此帧查看分配给的vCPU数 [!DNL New Relic] 显示应用程序名称。

## [!UICONTROL vCPU tier view over timeline]

![时间轴上的vCPU层视图](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

的 **[!UICONTROL vCPU tier view over timeline]** 此框架显示在超过24小时的选定时间范围内的vCPU层视图。 此帧查看分配给的vCPU数 [!DNL New Relic] 显示应用程序名称。 它将同时显示群集的上升大小和缩减大小。

## [!UICONTROL vCPU tier view over timeline BY NODE]

![按节点显示时间轴的vCPU层视图](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

的 **[!UICONTROL vCPU tier view over timeline BY NODE]** 帧按节点显示选定时间范围内的vCPU层视图。 此帧有助于检测节点丢失或节点大小调整或缩小时。 按节点显示时间轴的vCPU层视图，应查看时间轴少于24小时。

## [!UICONTROL Instance details]

![实例详细信息](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

的 **[!UICONTROL Instance details]** 表显示了每个 [!DNL New Relic] 应用程序。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![非响应节点](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

的 **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** 框架显示某个时间段内的非响应节点。
