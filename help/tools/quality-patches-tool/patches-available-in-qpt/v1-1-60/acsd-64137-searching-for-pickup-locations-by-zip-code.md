---
title: ACSD-64137：按邮政编码搜索取车位置不适用于荷兰语本地化
description: 应用ACSD-64137补丁程序，修复按邮政编码搜索接收位置不适用于荷兰语本地化的问题。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 86c28b6d-6584-4caf-bd35-13e0c1bdcf1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-64137：按邮政编码搜索取车位置不适用于荷兰语本地化

ACSD-64137修补程序修复了按邮政编码搜索接收位置不适用于荷兰语本地化的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60时，此修补程序可用。 修补程序ID为ACSD-64137。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

荷兰的邮政编码搜索未在前端结账页面上显示结果。 但是，它按城市运行，无需搜索即可显示相应的地址。

<u>重现步骤</u>：

1. 安装带有清单模块的干净实例。
1. 创建自定义库存。
1. 使用荷兰地址创建两个源，并将它们分配给库存（邮政编码7311ER和7311AE）。
1. 创建简单产品并添加库存。
1. 导航到&#x200B;**[!UICONTROL In-Store Delivery]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]**&#x200B;以启用&#x200B;**[!UICONTROL Delivery Methods]**。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**。 将&#x200B;**[!UICONTROL Provider]**&#x200B;设置为&#x200B;*脱机计算*。
1. 运行以下命令以导入NL国家/地区的地理名称。

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. 将产品添加到购物车并转到送货步骤。
1. 选择&#x200B;**[!UICONTROL Pick In Store]**。 然后，单击&#x200B;**[!UICONTROL Select Other]**&#x200B;以选择其他商店。
1. 在&#x200B;*搜索表单中键入* 7311 *或* 7311AE **[!UICONTROL Select Store]**。


**预期的结果**：

* 应填充匹配的存储。

**实际结果**：

* 未找到结果。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
