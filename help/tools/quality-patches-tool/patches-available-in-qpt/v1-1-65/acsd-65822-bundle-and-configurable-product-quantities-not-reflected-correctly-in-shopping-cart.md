---
title: ACSD-65822：捆绑包和可配置产品数量未在购物车中正确反映
description: 应用ACSD-65822修补程序以修复在添加捆绑产品时，管理面板的客户购物车部分中的数量显示为0的Adobe Commerce问题。
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '385'
ht-degree: 0%
---
# ACSD-65822： [!UICONTROL Shopping Cart]中未正确反映捆绑包和可配置产品数量

ACSD-65822修补程序修复了捆绑包和可配置产品数量在&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;下的&#x200B;**[!UICONTROL Shopping Cart]**&#x200B;部分中无法正确显示的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACSD-65822。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

捆绑包和可配置产品数量未正确显示在&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;下的&#x200B;**[!UICONTROL Shopping Cart]**&#x200B;部分中。

<u>重现步骤</u>：

1. 在店面创建用户。
2. 在管理面板中创建&#x200B;**[!UICONTROL Bundle product]**。
3. 在店面，作为登录用户，将捆绑产品添加到具有指定数量的购物车。
4. 在&#x200B;*管理员*&#x200B;面板中，转到&#x200B;**[!UICONTROL Customers]**&#x200B;并单击步骤1中所创建客户的&#x200B;**[!UICONTROL Edit]**。
5. 单击&#x200B;**[!UICONTROL Create Order]**。
6. 在左侧的&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;下，检查&#x200B;**[!UICONTROL Shopping Cart]**&#x200B;部分。 您应该会看到捆绑产品以及所选数量。

<u>预期的结果</u>：

捆绑项目数量应与店面上显示的数量匹配。

<u>实际结果</u>：

捆绑项目数量显示为0。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
