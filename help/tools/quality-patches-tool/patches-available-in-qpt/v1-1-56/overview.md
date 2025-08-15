---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.56
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.56中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.56

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.56中提供的修补程序所修复的问题。

QPT v1.1.56包含以下修补程序：

1. **ACSD-63244**：修复了JavaScript错误导致[!DNL Google Maps]无法正确呈现以及存在许多&#x200B;*未捕获的TypeError的问题：此问题。_each不是*&#x200B;面板中的控制台中的函数[!UICONTROL Admin]错误。
1. **ACSD-63242**：修复了在添加条目超过10,000个的目录产品时导入速度缓慢的问题。
1. **ACSD-63062**：修复了在应用多个重叠规则时购物车折扣计算不正确的问题。
1. **ACSD-62979**：修复了在GraphQL标头中使用错误[!UICONTROL Store ID]导致内存错误的问题。
1. **ACSD-62971**：修复了导入在&#x200B;*[!UICONTROL Quantity]*&#x200B;列中具有非数字值的库存源时导致&#x200B;*数量*&#x200B;设置为&#x200B;*0*&#x200B;的问题。
1. **ACSD-62872**：修复了计划更新验证不正确的唯一属性验证问题。
1. **ACSD-62755**：修复了[!DNL TinyMCE] 7要求在编辑器初始化设置中专门添加字体大小和字体的问题。
1. **ACSD-62670**：修复了[!UICONTROL Products Ordered]报表导出为CSV和XML时返回错误的问题。
1. **ACSD-62577**：通过优化查询索引和表索引，修复了店面搜索查询性能缓慢的问题。
1. **ACSD-62475**：修复了[!UICONTROL Gift Card]产品在购物车中错误合并的问题。
1. **ACSD-62428**：修复了当`is_out_of_stock`未设置为可搜索属性时，[!DNL SKU]在目录搜索索引中设置为不正确值的问题。
1. **ACSD-62355**：当可配置产品基于许多具有多个值的属性时，缩短可配置产品编辑页面的加载时间。
1. **ACSD-61805**：修复了通过[!DNL REST API]更新延交订单状态后，店面产品缺货的问题。
1. **ACSD-60811**：修复了在当前状态为&#x200B;*[!UICONTROL Processing]*&#x200B;或&#x200B;*[!UICONTROL Fraud]*&#x200B;的情况下，才可能使用自定义值或注释更新订单状态的问题。
1. **ACSD-62952**：修复了店面显示[!UICONTROL Gift Registry]日期不准确的问题。
1. **ACSD-55339**：修复了以下问题：以[!DNL SKU]0 *（零）开头的产品*&#x200B;删除了&#x200B;*0*，从而无法更新报价。

使用左侧的菜单导航到特定的修补程序页面。
