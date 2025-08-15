---
title: ACSD-65331：返回签出后，[!UICONTROL Pick in Store]中的选定存储已清除
description: 应用ACSD-65331修补程序以修复Adobe Commerce问题，该问题导致当用户反复返回签出页面时，清除[!UICONTROL Pick In Store]选项下选定的存储。
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331：返回签出后，**[!UICONTROL Pick in Store]**&#x200B;中的选定存储已清除

ACSD-65331修补程序修复了在用户反复返回签出页面时，清除&#x200B;**[!UICONTROL Pick In Store]**&#x200B;选项下所选存储的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACSD-65331。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户反复返回到签出页面时，**[!UICONTROL Pick In Store]**&#x200B;选项下的选定存储将被清除。

<u>重现步骤</u>：

1. 导航到&#x200B;**[!UICONTROL In-Store Delivery]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**&#x200B;以启用&#x200B;**[!UICONTROL In-Store Delivery]**。
1. 导航到[!DNL Google] > [!UICONTROL Google Distance Provider] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]**，为&#x200B;**[!UICONTROL Inventory]**&#x200B;配置有效的&#x200B;**[!UICONTROL Google Distance Provider]** API密钥。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**&#x200B;以添加包含以下详细信息的新源：

   * **[!UICONTROL Latitude]**： *41.917344*
   * **[!UICONTROL Longitude]**： *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**： *是*
   * **[!UICONTROL Country]**： *美国*
   * **[!UICONTROL State]**： *伊利诺伊州*
   * **[!UICONTROL City]**： *Carol流*
   * **[!UICONTROL Street]**： *E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**： *60188*

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]**&#x200B;以创建新库存。

   将新创建的源和主网站分配给此库存。
1. 编辑任何产品并：

   1. 将其分配给新创建的源。
   1. 将其状态设置为&#x200B;*[!UICONTROL In Stock]*，将数量设置为大于0。

1. 运行您的索引器。
1. 在店面，创建新客户并将加利福尼亚地址设置为默认帐单和送货地址。
1. 向同一客户添加一个附加的伊利诺伊地址（非默认）。
1. 将配置的产品添加到购物车并转到&#x200B;**[!UICONTROL Checkout]**。
1. 选择伊利诺伊地址，选择&#x200B;**[!UICONTROL Pick In Store]**&#x200B;作为送货方法，然后单击&#x200B;**[!UICONTROL Next]**。
1. 等待源加载并单击&#x200B;**[!UICONTROL Next]**。
1. 导航回主页。
1. 重新访问&#x200B;**[!UICONTROL Checkout]**&#x200B;页面。

<u>预期的结果</u>：

选定的存储应在&#x200B;**[!UICONTROL Pick In Store]**&#x200B;下保持可用。

<u>实际结果</u>：

装运步骤开始加载并重定向到&#x200B;**[!UICONTROL Pick In Store]**，但看不到商店。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
