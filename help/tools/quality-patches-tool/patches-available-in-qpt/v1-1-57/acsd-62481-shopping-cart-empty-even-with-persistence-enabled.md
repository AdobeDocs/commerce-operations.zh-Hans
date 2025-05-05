---
title: ACSD-62481：即使在启用[!UICONTROL Persistence]的情况下，购物车仍保持空白
description: 应用ACSD-62481修补程序以修复在结账期间使用登录弹出窗口时永久性购物车功能失败的Adobe Commerce问题。
feature: Shopping Cart, Checkout
role: Admin, Developer
source-git-commit: 27a98c42f2c514b3dd1a2f59c140b60b7ac26592
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-62481：即使在启用&#x200B;*[!UICONTROL Persistence]*&#x200B;的情况下，购物车仍保持空白

ACSD-62481修补程序修复了在签出期间使用登录弹出窗口时永久性购物车功能失败（因为它缺少&#x200B;*[!UICONTROL Remember Me]*&#x200B;复选框）导致产品在注销后从购物车中消失的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62481。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在签出期间使用登录弹出窗口时，持久购物车功能失败，因为它缺少&#x200B;*[!UICONTROL Remember Me]*&#x200B;复选框。 这会导致产品在注销后从购物车中消失。

<u>重现步骤</u>：

1. 在管理员中，按如下方式配置来宾帐户和永久性购物车设置：

   * 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**，并将&#x200B;*[!UICONTROL Allow Guest Checkout]*&#x200B;设置为&#x200B;*否*。

      * 单击&#x200B;**[!UICONTROL Save Config]**。

   * 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]**，并将&#x200B;*[!UICONTROL Enable Persistence]*&#x200B;设置为&#x200B;*是*。
   * 将所有其他设置保留为默认设置，但将&#x200B;*[!UICONTROL Clear Persistence on Sign Out]*&#x200B;更改为&#x200B;*否*。

      * 单击&#x200B;**[!UICONTROL Save Config]**。

1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]**&#x200B;将简单产品添加到目录。

   * 填写所需的最低详细信息并确保已有库存。

1. 在前端使用主表单`(../customer/account/create/)`创建客户帐户并注销。
1. 将产品作为访客添加到购物车。
1. 打开迷你购物车（右上角有图标），然后单击&#x200B;**[!UICONTROL View and Edit Cart]**。
1. 继续结帐。
1. 通过显示的弹出对话框登录到新客户帐户并注销。

<u>预期的结果</u>：

购物车会保留以前登录用户的产品。

<u>实际结果</u>：

* 购物车是空的。
* 弹出登录对话框不显示&#x200B;*[!UICONTROL Remember Me]*&#x200B;选项。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
