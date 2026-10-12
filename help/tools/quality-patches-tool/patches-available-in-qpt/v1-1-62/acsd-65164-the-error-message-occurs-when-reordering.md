---
title: ACSD-65164：选中单个复选框自定义选项的情况下重新订购可配置产品时出现错误消息
description: 应用ACSD-65164修补程序以修复Adobe Commerce问题，该问题导致使用单个选定的复选框自定义选项重新订购可配置产品时出现错误消息*某些选定的项目选项当前不可用*。
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%
---
# ACSD-65164：选中单个复选框自定义选项的情况下重新订购可配置产品时出现错误消息

ACSD-65164修补程序修复了以下问题：使用单个选定的复选框自定义选项重新订购可配置产品时，出现错误消息&#x200B;*某些选定的项目选项当前不可用*。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62时，此修补程序可用。 修补程序ID为ACSD-65164。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用单个选定的复选框自定义选项对可配置产品重新排序时，系统返回错误消息： *某些选定的项目选项当前不可用*。

### 要复制的步骤：

1. 在管理面板中，转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**。
1. 在&#x200B;**[!UICONTROL Customizable Options]**&#x200B;下，添加&#x200B;*复选框*&#x200B;选项。
   * 将复选框选项设置为&#x200B;*必需*。
   * 添加两个选项值。
1. 导航到Storefront并以注册客户身份登录。
1. 在选中一个复选框选项的情况下将产品添加到购物车。
1. 转到&#x200B;**[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**。
1. 转到&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]**&#x200B;以添加相同的产品。

**预期结果：**

产品应已成功添加到购物车。

**实际结果：**

将显示一条错误消息：

*无法将SKU为“24-MB01”的产品添加到购物车：某些选定的项目选项当前不可用。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
