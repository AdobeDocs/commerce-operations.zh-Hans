---
title: '[!UICONTROL Redis]选项卡'
description: 了解 [!DNL Observation for Adobe Commerce]的[!UICONTROL Redis]选项卡。
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 06f015139683f319f11317f8d7f0029cbd2548e3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# [!DNL Redis]选项卡

## [!UICONTROL Redis Node summary]

![Redis节点摘要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]**&#x200B;包含环境中的所有节点。 以上示例包括用于共享暂存的节点。 生产环境有一个主子项和两个子项，暂存环境也有一个主子项和两个子项。

## [!UICONTROL Redis node detail]

![Redis节点详细信息](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

**[!UICONTROL Redis node detail]**&#x200B;框架指示环境、[!DNL Redis]角色、软件版本和节点大小。

## [!UICONTROL Redis node roles timeline]

![Redis节点角色时间线](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

**[!UICONTROL Redis node roles timeline]**&#x200B;帧指示特定角色中丢失了[!DNL Redis]服务。 如果折线下降，则表示折线所表示的特定角色丢失了一个或多个节点。

## [!UICONTROL Connection to Redis]

![与Redis的连接](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

**[!UICONTROL Connection to Redis]**&#x200B;框架显示[!DNL New Relic Redis]示例数据中的net.connectedClients值。 它按[!DNL New Relic]应用程序（环境）和节点显示连接计数。

## [!UICONTROL Commands per second by node]

节点](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)每秒的![个命令

**[!UICONTROL Commands per second by node]**&#x200B;帧显示在所选时间范围内按节点每秒显示的[!DNL Redis]命令。

## [!UICONTROL Redis % of memory used]

已使用内存的![Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

**[!UICONTROL Redis % of memory used]**&#x200B;帧显示[!DNL Redis]服务器使用的最大内存的百分比。

## [!UICONTROL Redis used memory]

![Redis已用内存](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

**[!UICONTROL Redis used memory]**&#x200B;帧显示内存的节点使用率（以GB/MB为单位）。

## [!UICONTROL Redis changes since last db save]

自上次数据库保存后的![Redis更改](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis]驻留在内存中并将信息保存到存储中。 **[!UICONTROL Redis changes since last db save]**&#x200B;帧指示自上次数据库保存到存储后发生的内存更改次数。 有关[!DNL Redis's]持久性的详细说明，请参阅[Redis持久性](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/)。

## [!UICONTROL Redis synchronization from Log]

![Redis从日志同步](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

**[!UICONTROL Redis synchronization from Log]**&#x200B;帧侧重于在[!DNL Redis]同步期间遇到的错误或由于同步问题而发生的错误。 有关[!DNL Redis]的详细信息，请参阅[[!DNL Redis] 文档](https://redis.io/docs/)。
