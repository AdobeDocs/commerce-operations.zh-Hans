---
title: 此 [!UICONTROL Redis] 標籤
description: 瞭解 [!UICONTROL Redis] 索引標籤/ [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 此 [!DNL Redis] 標籤

## [!UICONTROL Redis Node summary]

![Redis節點摘要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

此 **[!UICONTROL Redis Node summary]** 包含環境中的所有節點。 上述範例包含共用中繼的節點。 生產環境有一個主要和兩個次要環境，中繼環境有一個主要和兩個次要環境。

## [!UICONTROL Redis node detail]

![Redis節點詳細資料](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

此 **[!UICONTROL Redis node detail]** 框架指示環境， [!DNL Redis] 角色、軟體版本和節點大小。

## [!UICONTROL Redis node roles timeline]

![Redis節點角色時間表](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

此 **[!UICONTROL Redis node roles timeline]** 影格指示遺失 [!DNL Redis] 特定角色中的服務。 如果折線下降，則表示折線所代表的特定角色已遺失一或多個節點。

## [!UICONTROL Connection to Redis]

![與Redis的連線](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

此 **[!UICONTROL Connection to Redis]** frame顯示來自以下專案的net.connectedClients值： [!DNL New Relic Redis] 範例資料。 它顯示連線計數依據 [!DNL New Relic] 應用程式（環境）和節點。

## [!UICONTROL Commands per second by node]

![節點每秒的命令數](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

此 **[!UICONTROL Commands per second by node]** 框架顯示 [!DNL Redis] 在選取的時間範圍內每秒按節點執行的命令。

## [!UICONTROL Redis % of memory used]

![已使用的記憶體的Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

此 **[!UICONTROL Redis % of memory used]** frame顯示 [!DNL Redis] 伺服器。

## [!UICONTROL Redis used memory]

![Redis已使用的記憶體](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

此 **[!UICONTROL Redis used memory]** frame顯示節點使用的記憶體(GB/MB)。

## [!UICONTROL Redis changes since last db save]

![自上次儲存資料庫以來的Redis變更](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] 是記憶體駐留，並將資訊儲存至儲存空間。 此 **[!UICONTROL Redis changes since last db save]** frame表示自上次資料庫儲存至儲存體後發生的記憶體變更次數。 請參閱 [Redis持續性](https://redis.io/docs/manual/persistence/) 如需更多說明，請參閱： [!DNL Redis's] 持續性。

## [!UICONTROL Redis synchronization from Log]

![記錄檔的Redis同步](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

此 **[!UICONTROL Redis synchronization from Log]** 框架著重於期間遇到的錯誤 [!DNL Redis] 同步或因同步問題而發生的錯誤。 如需詳細資訊，請參閱 [!DNL Redis]，請參閱 [[!DNL Redis] 檔案](https://redis.io/docs/).
