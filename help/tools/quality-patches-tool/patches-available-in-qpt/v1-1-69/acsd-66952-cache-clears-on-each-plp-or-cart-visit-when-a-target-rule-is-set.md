---
title: ACSD-66952：设置目标规则后，在每次访问PLP或购物车时缓存都会清除
description: 应用ACSD-66952修补程序以修复在设置了目标规则时每次PLP或购物车访问时都会清除缓存，从而造成不必要性能开销的Adobe Commerce问题。
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '387'
ht-degree: 0%
---
# ACSD-66952：设置目标规则后，在每次访问PLP或购物车时缓存都会清除

ACSD-66952修补程序修复了在每次PLP或购物车访问时清除缓存的问题，该问题会在设置目标规则时导致性能开销。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-66952。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在设置了目标规则时，每次PLP或购物车访问时都会清除缓存，从而导致性能开销的问题。

<u>重现步骤</u>：

1. 生成小型样本数据集。
1. 创建目标规则值，如下所示：
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *相关产品*
      * **[!UICONTROL Status]** = *活动*
      * **[!UICONTROL Apply to]** = *相关产品*
   1. **[!UICONTROL Products to Match]**
      * 保留为其默认值。
   1. **[!UICONTROL Products to Display]**
      * 如果这些条件中的&#x200B;**全部**&#x200B;为&#x200B;*true*，则设置&#x200B;**[!UICONTROL Product Category]** = *常量值111111*
1. 开始监控缓存失效请求的日志。
1. 访问产品页面。
1. 将产品添加到购物车并导航到购物车页面。

<u>预期的结果</u>：

在浏览网站时，应用程序不应使缓存失效。

<u>实际结果</u>：

缓存标记失效。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： Tools指南中用于优质修补程序的Self-service工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
