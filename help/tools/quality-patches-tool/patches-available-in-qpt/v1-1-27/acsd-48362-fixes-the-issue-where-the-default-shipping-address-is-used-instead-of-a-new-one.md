---
title: ACSD-48362：使用默认送货地址而不是新送货地址。
description: 应用ACSD-48362修补程序以修复以下问题：在使用可转让报价下订单时，使用Adobe Commerce的默认送货地址而不是新送货地址。
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%
---
# ACSD-48362：使用默认送货地址而不是新送货地址

ACSD-48362修补程序修复了在使用可协商的报价下订单时使用默认送货地址而不是新添加的地址的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-48362。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用可转让报价下订单时，将使用默认送货地址而不是新添加的送货地址。

<u>重现步骤</u>：

1. 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**&#x200B;以启用B2B报价。
1. 以公司用户身份登录。
1. 将产品添加到购物车。
1. 转到购物车页面并请求报价。
1. 转到客户的&#x200B;**[!UICONTROL My Quotes]**&#x200B;页面，然后选择刚刚创建的报价。
1. 转到客户报价页的&#x200B;**[!UICONTROL Shipping Information]**&#x200B;部分。
   * 单击&#x200B;**[!UICONTROL Add New Address]**，填写表单，然后保存地址（不要选择&#x200B;**[!UICONTROL Use as my default billing address]**&#x200B;或&#x200B;**[!UICONTROL Use as my default shipping address]**）。
1. 单击客户报价页上的&#x200B;**[!UICONTROL Send for Review]**。
1. 以管理员用户身份转到Adobe Commerce管理员，打开刚创建的报价，然后单击&#x200B;**[!UICONTROL Send]**。
1. 现在转到客户的报价页面，刷新该页面，然后单击&#x200B;**[!UICONTROL Proceed to Checkout]**。
1. 在结账页面上，即使选择了新的送货地址，数据也会显示默认送货地址。
1. 单击&#x200B;**[!UICONTROL Continue]**&#x200B;并下订单。

<u>预期的结果</u>：

订单应使用新地址，而无需在结账页面上重新选择默认送货地址。

<u>实际结果</u>：

使用默认送货地址下订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
