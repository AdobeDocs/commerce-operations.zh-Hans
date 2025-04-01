---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.61
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.61中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 0800285df83eb3e3ffcfb003bf984248b750db32
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.61

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.61中提供的修补程序所修复的问题。

QPT v1.1.61包含以下修补程序：

1. **ACP2E-3689**：修复了在较深级别显示类别树并反映锚点/非锚点关系的多个问题。
1. **ACP2E-3705**：修复了在设置`MAGE_INDEXER_THREADS_COUNT`时`indexer_update_all_views` cron执行失败的问题。
1. **ACSD-63883**：修复了[!DNL GraphQL]响应中[!UICONTROL Requisition List]返回错误的`items_count`的问题。
1. **ACSD-63974**：通过将分页功能添加到店面的[!UICONTROL Requisition List]网格中（该网格仅显示限制每页记录数的记录部分，而不是一次显示所有记录），修复了在项目过多时[!UICONTROL Requisition List]页面加载时间过长的问题。
1. **ACSD-64178**：修复了存在数千个产品属性时[!UICONTROL Attribute Set]编辑页面加载缓慢的问题。
1. **ACSD-64209**：修复了Cron计划程序检索所有可协商引号而不排除状态为&#x200B;**[!UICONTROL ordered]**&#x200B;的可协商引号导致触发电子邮件或电子邮件的问题。
1. **ACSD-64431**：请求中包含优惠券代码信息的`placeOrder`突变不再引发内部错误，而是表明已成功下订单。
1. **ACSD-64467**：修复了在商店视图级别保存类别描述后WYSIWYG编辑器显示为空的问题。
1. **ACSD-64546**：修复了在创建UPS配送标签期间UI中出现一般错误消息，并在日志中存储&#x200B;*阵列到字符串转换*&#x200B;异常的问题，从而确保在UI中显示实际错误，并在日志中存储正确的错误消息。
1. **ACSD-64684**：修复了在编辑和保存值大于&#x200B;*999*&#x200B;的礼品卡时由于数字&#x200B;*一千(1,000)*&#x200B;中的逗号（千位分隔符）而发生验证错误的问题。

使用左侧的菜单导航到特定的修补程序页面。
