---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.77
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.77中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 98ccb5c357ebcb3bc2a7bb48e61b8557a65049f9
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.77

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.77中提供的修补程序所修复的问题。

QPT v1.1.77包含以下修补程序：

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)**：修复了显示错误价格的问题，因为无法清除[!DNL Redis]缓存。
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)**：修复了在加载PDP期间，当在存储区中创建多个客户区段时，`X-Magento-Vary`个Cookie设置多次的问题。
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)**：修复了签出性能随客户区段数量增加而降低的问题。
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)**：修复了在尝试预览具有自定义域的商店的内容时，计划更新预览中断的问题。
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)**：修复了在使用阿拉伯语区域设置并将出生日期(DOB)属性设置为显示在店面时，创建客户帐户失败的问题。
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)**：修复了无法从[!DNL Fastly]缓存正确存储或提供可缓存页面的问题，该问题会导致缓存行为不一致并降低了性能。
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)**：修复了在不同时区创建的网站的特殊价格未生效的问题。
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)**：修复了当某个可配置产品的任何子产品满足筛选条件时，该产品会自动包含在[!DNL Page Builder]产品轮播列表中的问题。
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)**：修复了通过`sales_*_async_insert` cron作业可处理和插入的条目数限制为每次&#x200B;*100*&#x200B;的问题。
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)**：修复了在从发票创建部分退款时（如果先前已从订单视图页面创建贷项通知单），贷项通知单中计税不正确的问题。
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)**：修复了礼品卡余额和到期日期未按照分配的网站范围显示的问题。
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)**：修复了异步退款操作的一个问题，该问题导致无法正确处理带有`is_online`参数的退款请求。

使用左侧的菜单导航到特定的修补程序页面。
