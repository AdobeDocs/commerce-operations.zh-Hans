---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.51
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.51中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 277b6301-944b-4913-84a3-bbcca2c92ce1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.51

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.51中提供的修补程序所修复的问题。

QPT v1.1.51包含以下修补程序：

1. **ACSD-59786**：修复了在尝试获取已过期报价的报价ID时，GraphQL返回内部服务器错误的问题。
1. **ACSD-60234**：修复了在通过付款方式应用折扣时，[!DNL PayPal]上显示不正确金额的问题。
1. **ACSD-59967**：修复了JavaScript错误导致[!DNL Google Maps]无法正确呈现的问题。
1. **ACSD-60326**：修复了GraphQL查询客户退货状态时出现错误的问题。
1. **ACSD-60538**：修复了以下问题：如果某个产品在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中处于禁用状态，并且只在特定商店视图范围内启用，则产品属性在GraphQL响应中无法正确显示，从而导致产品无法正确显示。
1. **ACSD-60631**：修复了将同一简单产品分配给多个可配置产品时，GraphQL返回错误的问题。
1. **ACSD-60632**：修复了在每次尝试下订单时都保存新地址的问题，无论是否成功创建了订单。
1. **ACSD-60816**：修复了APM代理插入的[!DNL New Relic Browser Monitoring]脚本与CSP（内容安全策略）不兼容，从而阻止其执行的问题。
1. **ACSD-61195**：修复了在购物车GraphQL请求的最后一页上未返回购物车项目的问题。

使用左侧的菜单导航到特定的修补程序页面。
