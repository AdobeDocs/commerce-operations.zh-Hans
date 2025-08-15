---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.31
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.31中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.31

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.31中提供的修补程序所修复的问题。

QPT v1.1.31包含以下修补程序：

1. **ACSD-50817**：通过为引用表中的`sales_clean_quotes`和`store_id`列添加复合索引，优化cron作业`updated_at`以更快地运行。
1. **ACSD-50345**：修复了以下问题：[!DNL Google reCAPTCHA v2]在提交失败的付款后未重新加载，[!DNL Google reCAPTCHA v3 Invisible]无法正常进行结帐，无法下订单，以及未触发[!UICONTROL PlaceOrder]事件。
1. **ACSD-49392**：修复了在部分退款捆绑产品后，订单状态更改为“已关闭”的问题。
1. **ACSD-51036**：修复了并发REST API调用期间的争用条件导致[!UICONTROL Items Ordered]表中装运状态信息覆盖的问题。
1. **ACSD-50858**：修复了在信用卡付款失败后优惠券被错误地标记为使用的问题。

使用左侧的菜单导航到特定的修补程序页面。
