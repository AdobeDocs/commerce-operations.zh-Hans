---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.64
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.64中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: e86b8557-a14a-40e2-a181-56efa4383a1c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.64

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.64中提供的修补程序所修复的问题。

QPT v1.1.64包含以下修补程序：

1. **ACP2E-3838**：修复了[!DNL Page Builder] CORS错误导致无法在生产模式的管理面板中保存更改的问题。
1. **ACP2E-3841**：修复了在使用`subselect`条件并启用&#x200B;**[!UICONTROL Free Shipping]**&#x200B;的情况下，多配送产品的购物车价格规则无法正确应用的问题。
1. **ACSD-63139**：修复了当产品属性包含数千个选项值时产品导出失败的问题。
1. **ACSD-65100**：修复了在映像优化过程中删除&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;配置中&#x200B;**[!UICONTROL Maximum Width]**&#x200B;和&#x200B;**[!UICONTROL Maximum Height]**&#x200B;的值导致错误的问题。
1. **ACSD-65127**：修复了在生产模式下启用JavaScript缩小会导致[!DNL TinyMCE] 6在浏览器控制台中生成错误，从而影响功能和用户体验的问题。
1. **ACSD-65787**：修复了在架构创建或更新期间`SchemaBuilder`类在处理表数据时由于未定义数组键&#x200B;*column*&#x200B;而崩溃的问题。
1. **ACSD-65223**：修复了为[!DNL B2B]采购订单手动选择条款和协议导致错误的问题。
1. **ACSD-65540**：修复了在更新`company_structure`表时由于缺少`REGEXP_LIKE`函数而发生SQL语法错误的问题。
1. **ACSD-65684**：修复了在更新到[!DNL B2B] 1.5.2后升级`Magento_Company`模块时，处理`company_structure`表中的大量记录(~100,000+)所花费的时间过长的性能问题。

使用左侧的菜单导航到特定的修补程序页面。
