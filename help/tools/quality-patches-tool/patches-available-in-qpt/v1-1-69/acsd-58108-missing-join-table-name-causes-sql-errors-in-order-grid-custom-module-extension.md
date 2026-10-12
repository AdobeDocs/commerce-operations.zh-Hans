---
title: ACSD-58108：由于缺少联接表名称，导致网格自定义模块扩展顺序出现SQL错误
description: 应用ACSD-58108修补程序以修复Adobe Commerce问题，该问题导致在筛选某些列时顺序网格自定义模块扩展中缺少联接表名称导致SQL错误。
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
exl-id: 1195e1c3-575c-48d6-8a10-c300f9bbb84a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
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
source-wordcount: '388'
ht-degree: 0%
---
# ACSD-58108：由于缺少联接表名称，导致网格自定义模块扩展顺序出现SQL错误

ACSD-58108修补程序修复了在筛选某些列时，顺序网格自定义模块扩展中缺少联接表名称会导致SQL错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-58108。 请注意，此问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用自定义模块扩展时，原始提取表中缺少联接表名称会导致顺序网格出现SQL错误。 出现此问题的原因是，在加入&#x200B;**[!UICONTROL sales_order_item]**&#x200B;表后，`addFilterToMap`函数对某些列不起作用，导致筛选时出错。

<u>重现步骤</u>：

01. 安装2.4版本的开发实例。
02. 创建新订单。
03. 安装带有SQL扩展的自定义模块。
04. 导航到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
05. 应用&#x200B;**[!UICONTROL Purchase Date]**&#x200B;筛选器并等待结果。
06. 应用&#x200B;**[!UICONTROL Product SKU]**&#x200B;筛选器。

<u>预期的结果</u>：

在订单网格中过滤订单的工作方式不会出错。

<u>实际结果</u>：

在顺序网格中应用过滤器时出错。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
