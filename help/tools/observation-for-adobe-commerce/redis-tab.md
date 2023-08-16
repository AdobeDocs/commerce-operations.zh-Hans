---
title: 此 [!UICONTROL Redis] 选项卡
description: 了解 [!UICONTROL Redis] 选项卡/ [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 此 [!DNL Redis] 选项卡

## [!UICONTROL Redis Node summary]

![Redis节点摘要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

此 **[!UICONTROL Redis Node summary]** 包含环境中的所有节点。 以上示例包括用于共享暂存的节点。 生产环境有一个主子项和两个子项，暂存环境也有一个主子项和两个子项。

## [!UICONTROL Redis node detail]

![Redis节点详细信息](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

此 **[!UICONTROL Redis node detail]** 帧指示环境， [!DNL Redis] 角色、软件版本和节点大小。

## [!UICONTROL Redis node roles timeline]

![Redis节点角色时间线](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

此 **[!UICONTROL Redis node roles timeline]** 帧指示丢失 [!DNL Redis] 特定角色中的服务。 如果折线下降，则表示折线所表示的特定角色丢失了一个或多个节点。

## [!UICONTROL Connection to Redis]

![与Redis的连接](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

此 **[!UICONTROL Connection to Redis]** 框架显示来自以下位置的net.connectedClients值： [!DNL New Relic Redis] 示例数据。 它显示连接计数依据 [!DNL New Relic] 应用程序（环境）和节点。

## [!UICONTROL Commands per second by node]

![按节点每秒的命令数](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

此 **[!UICONTROL Commands per second by node]** 框架显示 [!DNL Redis] 选定的时间范围内每秒按节点列出的命令。

## [!UICONTROL Redis % of memory used]

![占已用内存的红色%](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

此 **[!UICONTROL Redis % of memory used]** frame显示 [!DNL Redis] 服务器。

## [!UICONTROL Redis used memory]

![Redis已用内存](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

此 **[!UICONTROL Redis used memory]** 帧显示节点内存使用率（以GB/MB为单位）。

## [!UICONTROL Redis changes since last db save]

![自上次数据库保存以来的Redis更改](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] 驻留在内存中，并将信息保存到存储。 此 **[!UICONTROL Redis changes since last db save]** frame表示自上次将数据库保存到存储后发生的内存更改次数。 请参阅 [Redis持久性](https://redis.io/docs/manual/persistence/) 有关更多说明，请参阅 [!DNL Redis's] 持久性。

## [!UICONTROL Redis synchronization from Log]

![从日志进行Redis同步](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

此 **[!UICONTROL Redis synchronization from Log]** 帧侧重于期间遇到的错误 [!DNL Redis] 同步或由于同步问题而发生的错误。 有关的详细信息 [!DNL Redis]，请参阅 [[!DNL Redis] 文档](https://redis.io/docs/).
