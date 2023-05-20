---
title: 此 [!DNL Infra] 標籤
description: 此 [!DNL Infra] 索引標籤可隔離基礎架構問題的問題和原因。
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 此 [!DNL Infra] 標籤

此 **[!DNL Infra]** 索引標籤可隔離基礎架構問題的問題和原因。 進一步說明您可以在標籤上看到的影格。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![服務警示](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

此 **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** 圖表顯示由收集的服務警示 [!DNL New Relic] 基礎結構代理程式。 這會顯示服務重新啟動，其中許多與部署有關。

## [!UICONTROL Inode usage by mount]

![依掛載區分的資訊節點使用狀況](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

此 **[!UICONTROL Inode usage by mount]** 影格顯示 [!DNL inode] 在選取的時間範圍內透過掛載的使用量。 即使節點用完後可能有大量可用儲存空間 [!DNL inodes]，則會顯示缺少可用的儲存空間。 移除檔案（尤其是小型檔案）會釋放空間並讓 [!DNL inodes] 可用。

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vCPU層級檢視時間軸大於2週](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

此 **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** 影格會顯示選取超過兩週的時間範圍內的vCPU層檢視。 此框架會檢視指派給的vCPU數量 [!DNL New Relic] 顯示應用程式名稱。

## [!UICONTROL vCPU tier view over timeline]

![vCPU層檢視時間表](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

此 **[!UICONTROL vCPU tier view over timeline]** 影格會顯示所選時間範圍內超過24小時的vCPU層檢視。 此框架會檢視指派給的vCPU數量 [!DNL New Relic] 顯示應用程式名稱。 它會顯示叢集向上和向下移動。

## [!UICONTROL vCPU tier view over timeline BY NODE]

![依節點的vCPU層檢視時間軸](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

此 **[!UICONTROL vCPU tier view over timeline BY NODE]** 框架會依節點顯示所選時間範圍內的vCPU層檢視。 此框架有助於偵測節點遺失，或節點已放大或縮小時。 依節點的vCPU層級檢視時間軸，應檢視少於24小時的時間軸。

## [!UICONTROL Instance details]

![執行個體詳細資訊](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

此 **[!UICONTROL Instance details]** 表格顯示每個執行處理的詳細資訊 [!DNL New Relic] 應用程式。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![無回應節點](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

此 **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** 框架顯示一段時間內無回應的節點。
