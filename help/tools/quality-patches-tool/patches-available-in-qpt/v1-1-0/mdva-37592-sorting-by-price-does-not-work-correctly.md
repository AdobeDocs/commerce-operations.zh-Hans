---
title: MDVA-37592：按价格排序不适用于价格为零的产品
description: MDVA-37592 Adobe Commerce修补程序解决了按价格排序对分配给共享目录且价格为零的产品无法正常工作的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0后，即可使用此修补程序。 修补程序ID为MDVA-37592。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%
---
# MDVA-37592：按价格排序不适用于价格为零的产品

MDVA-37592 Adobe Commerce修补程序解决了按价格排序对分配给共享目录且价格为零的产品无法正常工作的问题。 安装[Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.0时，此修补程序可用。 修补程序ID为MDVA-37592。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署类型） 2.3.6-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于分配给共享目录且价格为零的产品，按价格排序无法正确运行。

<u>先决条件</u>：

已安装B2B。

<u>重现步骤</u>：

1. 启用共享目录。
1. 使用以下价格创建四个产品，并将它们分配给一个类别 — $50、$60、$70和$80。
1. 使用上述产品创建共享目录。
1. 将价格为$70的产品自定义价格设置为零。
1. 现在创建公司用户，并将其分配给刚刚创建的共享目录。
1. 使用公司帐户登录，并浏览到产品被分配到的类别。
1. 尝试按价格排序。

<u>预期的结果</u>：

对价格为零的产品进行了正确排序。

<u>实际结果</u>：

价格为零的产品未正确排序。 而是按照原价排序。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!DNL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
