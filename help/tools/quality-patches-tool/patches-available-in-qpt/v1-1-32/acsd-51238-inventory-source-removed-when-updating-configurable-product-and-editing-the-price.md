---
title: ACSD-51238：在更新可配置产品和编辑价格时，将删除库存来源
description: 应用ACSD-51238修补程序以修复在更新可配置产品和编辑价格时删除库存来源的Adobe Commerce问题。
feature: Configuration, Inventory, Orders, Products
role: Admin
exl-id: 785f012f-e064-4ac6-b559-9e9aa42c679c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-51238：在更新可配置产品和编辑价格时，将删除库存来源

ACSD-51238修补程序修复了在更新可配置产品和编辑价格时删除库存来源的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51238。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在更新可配置产品和编辑价格时，将删除库存来源。

<u>重现步骤</u>：

1. 安装&#x200B;**[!DNL Adobe Commerce]**&#x200B;和&#x200B;**[!DNL Inventory module]**
1. 转到&#x200B;**[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]**&#x200B;并创建&#x200B;*两个源*&#x200B;和&#x200B;*两个库存*。
1. 创建一个&#x200B;**[!UICONTROL configurable product]**&#x200B;并将其分配给&#x200B;**[!UICONTROL default sources]**&#x200B;或&#x200B;**[!UICONTROL newly created sources]**。
1. 单击&#x200B;**[!UICONTROL next button]**&#x200B;并&#x200B;*保存*&#x200B;产品。
1. 现在编辑同一&#x200B;**[!UICONTROL Configurable Product]**&#x200B;并单击&#x200B;**[!UICONTROL Configuration tab]**&#x200B;中的&#x200B;**[!UICONTROL Edit Configuration]**。
1. 在`Step 3: Bulk Images,Price and Quantity`中，更改`price`并分别将`Quantity`和`Images`保留为`Skip quantity at this time`和`Skip image uploading at this time`。
1. 单击&#x200B;**[!UICONTROL next button]**&#x200B;并生成产品。

<u>预期的结果</u>

**[!UICONTROL Configuration tab]**&#x200B;内每个源的数量不应为空。

<u>实际结果</u>

**[!UICONTROL Configuration tab]**&#x200B;中每个源的数量为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
