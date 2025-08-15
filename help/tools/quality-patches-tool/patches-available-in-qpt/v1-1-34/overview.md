---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.34
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.34中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.34

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.34中提供的修补程序所修复的问题。

QPT v1.1.34包含以下修补程序：

1. **ACSD-52277**：修复了在管理员中创建新订单时，管理员用户在选择商店视图后未正确重定向的问题。
1. **ACSD-50813**：修复了管理员无法在具有[!UICONTROL Add Products by SKU]功能的SKU中将包含斜杠的捆绑产品添加到管理员订单中的问题。
1. **ACSD-51630**：修复了大量系统消息导致下载管理员页面变慢的问题。
1. **ACSD-51853**：修复了在使用[!DNL Page Builder]时未应用复制的文本样式的问题。
1. **ACSD-52160**：修复了根据规则条件&#x200B;*如果在购物车中找到/未找到项目，并且所有条件均为true*，则无法正确评估购物车价格规则的产品验证结果的问题。
1. **ACSD-51636**：修复了以下问题：尽管拥有所有必要的角色和权限，管理员仍无法从客户帐户部分添加新用户。
1. **ACSD-51739**：修复了在`structure_id` GraphQL请求中请求`CompanyTeam`时返回错误的问题。
1. **ACSD-51857**：修复了`aggregate_sales_report_bestsellers_data` cron报告性能缓慢影响大型`sales_order`和`sales_order_item`数据库表的问题。
1. **ACSD-48448**：修复了在订单取消期间发生争用条件问题，该问题导致&#x200B;*inventory_reservation*&#x200B;表中出现重复条目。
1. **ACSD-52689**：修复了使用REST API无法将图像上传到[!DNL Amazon S3]存储的问题。

使用左侧的菜单导航到特定的修补程序页面。
