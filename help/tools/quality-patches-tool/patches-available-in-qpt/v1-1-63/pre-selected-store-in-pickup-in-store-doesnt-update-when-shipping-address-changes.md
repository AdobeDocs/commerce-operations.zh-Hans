---
title: 发送地址更改时，“店内提货”中预先选定的商店不会更新
description: 应用ACSD-64753修补程序以修复在所选商店的服务半径之外输入新送货地址时预选商店未更新的Adobe Commerce问题。
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-64753：配送地址更改时，“店内提货”中预先选定的商店不会更新

ACSD-64753修补程序修复了在所选商店的服务半径之外输入新送货地址时预选商店未更新的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63时，此修补程序可用。 修补程序ID为ACSD-64753。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在所选商店的服务半径之外输入新送货地址时，预选商店未更新。

<u>重现步骤</u>：

1. 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;以启用&#x200B;**[!UICONTROL In-Store Delivery]**。
1. 为[!DNL Google Distance Provider]提供有效的[!DNL Google] API密钥。 为此，请导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**。
1. 添加新源(**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**)，并设置以下值：
   * **[!UICONTROL Latitude]**： *-41.917344*
   * **[!UICONTROL Longitude]**： *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**： *是*
   * **[!UICONTROL Country United]**： *状态*
   * **[!UICONTROL State]**： *伊利诺伊州*
   * **[!UICONTROL City]**： *Carol流*
   * **[!UICONTROL Postcode]**： *60188*
1. 添加新库存(**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**)，为其分配新来源和主网站。
1. 编辑任何产品，将该产品分配给新Source，库存和数量> *0*。
1. 等待重新索引完成。
1. 在店面，创建新客户，然后添加一个加利福尼亚地址作为默认帐单和送货地址。
1. 向此客户添加另一个非默认伊利诺伊地址。
1. 将产品添加到购物车并继续结帐。
1. 保持选中加利福尼亚配送地址，然后选择&#x200B;**[!UICONTROL Pick in Store]**&#x200B;配送方式。 单击&#x200B;**[!UICONTROL Next]**。

<u>预期的结果</u>：

由于加利福尼亚地址在最大搜索半径（200公里）之外，因此客户不应使用伊利诺伊州Source。

<u>实际结果</u>：

可以挑选伊利诺伊州的货源，客户可以继续结帐。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
