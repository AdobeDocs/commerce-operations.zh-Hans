---
title: ' [!DNL Infra] 选项卡'
description: ' [!DNL Infra] 选项卡可隔离基础架构问题的问题和原因。'
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Infra]选项卡

**[!DNL Infra]**&#x200B;选项卡可隔离基础架构问题的问题和原因。 对您可在选项卡上看到的帧进行了进一步的描述。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![服务警报](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

**[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]**&#x200B;图形显示[!DNL New Relic]基础结构代理收集的服务警报。 这将显示服务重新启动，其中许多与部署关联。

## [!UICONTROL Inode usage by mount]

![装载的Inode使用量](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

**[!UICONTROL Inode usage by mount]**&#x200B;帧显示所选时间范围内按装载显示的[!DNL inode]使用情况。 即使可能有大量可用存储，但如果节点用完[!DNL inodes]，则会显示缺少可用存储。 删除文件（尤其是小文件）将释放两个空间并使[!DNL inodes]可用。

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vCPU层在时间线上的查看时间大于2周](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

**[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]**&#x200B;帧在超过两周的选定时间范围内显示vCPU层视图。 此框架查看分配给所显示[!DNL New Relic]应用程序名称的vCPU数。

## [!UICONTROL vCPU tier view over timeline]

![vCPU层查看时间线](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

**[!UICONTROL vCPU tier view over timeline]**&#x200B;帧在超过24小时的选定时间范围内显示vCPU层视图。 此框架查看分配给所显示[!DNL New Relic]应用程序名称的vCPU数。 它将同时显示群集的上升和下降。

## [!UICONTROL vCPU tier view over timeline BY NODE]

按节点![在时间线上查看](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)vCPU层

**[!UICONTROL vCPU tier view over timeline BY NODE]**&#x200B;帧按节点显示选定时间范围内的vCPU层视图。 此帧有助于检测节点丢失情况或节点放大或缩小情况。 vCPU层按节点查看时间线，应查看不到24小时的时间线。

## [!UICONTROL Instance details]

![实例详细信息](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

**[!UICONTROL Instance details]**&#x200B;表显示每个[!DNL New Relic]应用程序的实例详细信息。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![无响应节点](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

**[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]**&#x200B;帧显示一段时间内无响应的节点。
