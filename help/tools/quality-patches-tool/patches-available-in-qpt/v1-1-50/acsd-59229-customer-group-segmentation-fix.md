---
title: ACSD-59229：由于X-Magento-Vary值已过时，导致客户组数据分配错误
description: 应用ACSD-59229修补程序以修复Adobe Commerce问题，该问题导致与客户组相关的信息被保存在错误的区段中，因为请求中的X-Magento-Vary值已过期。
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
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
source-wordcount: '496'
ht-degree: 1%
---
# ACSD-59229：由于X-Magento-Vary值已过时，导致客户组数据分配错误

ACSD-59229修补程序修复了客户组相关信息因请求中的过时X-Magento-Vary值而保存在错误区段中的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-59229。 请注意，此问题已在2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于请求中的X-Magento-Vary值已过期，因此将客户组相关信息保存在错误的区段中。

<u>先决条件</u>：

确保已安装包含示例数据的Adobe Commerce B2B并配置了[!DNL Varnish]。

<u>重现步骤</u>：

1. 为[!DNL SKU 24-MB01]设置高级定价：
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *批发* = *$200*
      * *Retailer* = *$30*

1. 创建两个客户帐户。
1. 将两个客户分配给&#x200B;**批发**&#x200B;组。
1. 打开两个不同的浏览器会话并与每个客户登录。
1. 导航到每个客户的&#x200B;**[!UICONTROL 24-MB01]**&#x200B;产品页面，并验证显示的价格是否为&#x200B;*$200*。
1. 将其中一个客户的客户组更改为&#x200B;**零售业**。
1. 使用以下命令清除缓存： `bin/magento cache:flush full_page`。
1. 刷新每个客户的产品页面。

<u>预期的结果</u>：

1. 零售客户可以看到产品的正确价格&#x200B;*$30*。
1. 批发客户可以看到产品的&#x200B;*$200*&#x200B;的正确价格。

<u>实际结果</u>：

1. 零售客户可以看到产品的正确价格&#x200B;*$30*。
1. 批发客户看到产品的&#x200B;*$30*（零售价）的价格不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
