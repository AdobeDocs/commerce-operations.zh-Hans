---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.48中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.48

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.48中提供的修补程序所修复的问题。

QPT v1.1.48包含以下修补程序：

1. **ACSD-55566**：修复了在合并源购物车和目标购物车具有相同的捆绑项目时，*[!UICONTROL mergeCart mutation]*&#x200B;在GraphQL响应中失败并出现&#x200B;*内部服务器错误*&#x200B;的问题。
1. **ACSD-56546**：修复了禁用&#x200B;*[!UICONTROL Display Out of Stock Product]*&#x200B;配置时，可配置和捆绑产品在店面中显示为&#x200B;*[!UICONTROL Out of Stock]*&#x200B;的问题。
1. **ACSD-56635**：修复了在将[!UICONTROL Account Sharing]设置为&#x200B;*[!UICONTROL Global]*&#x200B;的情况下使用导入时，导入的客户使用相同的电子邮件地址重复的问题。
1. **ACSD-56741**：修复了错误消息&#x200B;*当数据库包含与索引机制和[!DNL MView]无关的自定义MySQL触发器时，尝试访问`setup:upgrade`期间显示的null*&#x200B;类型的值的数组偏移。
1. **ACSD-57315**：修复了每次在[!UICONTROL Admin]的查看事务屏幕上单击&#x200B;**[!UICONTROL Fetch]**&#x200B;按钮时，[!DNL PayPal Payflow Pro]中都会创建一个新事务的问题。
1. **ACSD-57337**：修复了具有特定网站访问限制的管理员用户能够查看&#x200B;*[!UICONTROL Companies]*&#x200B;网格中所有网站的公司的问题。
1. **ACSD-57394**：修复了GraphQL中按多个排序字段对产品排序不正确的问题。
1. **ACSD-57565**：修复了在更新时间段之前&#x200B;*[!UICONTROL Order]*&#x200B;仪表板显示错误订单信息的问题。 现在，仪表板在首次加载时显示正确的订单统计信息。
1. **ACSD-57854**：修复了产品GraphQL请求在类别聚合中返回禁用类别的问题。
1. **ACSD-58008**：修复了在未指定结束日期的情况下更新计划更新会删除暂存项目的先前版本的问题。

使用左侧的菜单导航到特定的修补程序页面。

