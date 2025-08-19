---
title: ACSD-62146：选定的账单地址在结账付款页面上消失
description: 应用ACSD-62146修补程序以修复Adobe Commerce问题：如果启用了地址搜索并且“客户地址数限制”设置为1，则选定的账单地址将在结账付款页面上消失。
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146：选定的账单地址在结账付款页面上消失

ACSD-62146修补程序修复了在启用地址搜索并将[!UICONTROL Number of Customer Addresses Limit]设置为1时，所选帐单地址在签出付款页面上消失的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-62146。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用地址搜索并将&#x200B;**[!UICONTROL Number of Customer Addresses Limit]**&#x200B;设置为1时，选定的帐单地址将在结帐付款页面上消失。

<u>重现步骤</u>：

1. 要启用地址搜索，请转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**。
1. 将&#x200B;**[!UICONTROL Number of Customer Addresses Limit]**&#x200B;设置为1。
1. 创建一个客户并添加两个不同的地址。
1. 将产品添加到购物车并继续结帐。
1. 单击&#x200B;**[!UICONTROL Change Address]**&#x200B;并使用弹出窗口更改地址。
1. 选择地址2作为送货地址。
1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;以继续执行付款步骤。
1. 验证帐单地址和送货地址是否相同。
1. 刷新页面而不进行付款。

<u>预期的结果</u>：

如果帐单地址和送货地址相同，则显示送货地址。

<u>实际结果</u>：

默认帐单地址和选定的送货地址不可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
