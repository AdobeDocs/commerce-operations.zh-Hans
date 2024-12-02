---
title: ACSD-58735：受限管理员无法查看相关网站客户帐户上放弃的购物车
description: 应用ACSD-58735修补程序以修复Adobe Commerce问题，该问题导致受限管理员无法在关联网站的Commerce管理员中查看客户帐户页面上的放弃的购物车。
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
source-git-commit: 8a33e0aadf3aab2b267f18b20a5195538b6990ef
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-58735：受限管理员无法查看相关网站客户帐户上放弃的购物车

ACSD-58735修补程序修复了以下问题：具有受限角色的管理员用户无法从Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]**&#x200B;选项卡查看已放弃客户的购物车。

出现此问题的原因是，在显示多个网站的网格视图时，如果默认情况下在“管理”面板中加载了放弃的购物车，则不会显示关联的商店ID。

安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-58735。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

受限管理员无法在管理员面板中的客户帐户页面上查看放弃的购物车。

<u>重现步骤</u>：

1. 创建只能访问其中一个网站的管理员角色。
1. 创建放弃的购物车。
1. 以具有完整权限的管理员用户身份登录。 检查&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**，查看购物车是否显示。
1. 将&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**&#x200B;作为受限管理员用户选中。

<u>预期的结果</u>：

受限制的管理员可以看到相关网站中已放弃的购物车。

<u>实际结果</u>：

受限管理员看不到关联网站的已放弃购物车。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
