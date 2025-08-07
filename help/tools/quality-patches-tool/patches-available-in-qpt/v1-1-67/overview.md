---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.67
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.67中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 47f6b57d-b945-4e77-8630-2df709a3469e
source-git-commit: 6758b85e797de75ea5430062c8335fa903f00838
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.67

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.67中提供的修补程序所修复的问题。

QPT v1.1.67包含以下修补程序：
1. **AC-14985**：使用TLS发送SMTP电子邮件时出错。
1. **AC-14984**： php-amqplib/php-amqplib ^3.2.0的SSL连接问题。
1. **ACSD-65935**： `customerOrders` GraphQL查询在删除产品时返回内部服务器错误。
1. **ACSD-66049**：非英语店面显示不正确的定价，原因是ICU库版本。
1. **ACSD-66084**： `row_total_incl_tax`对于订单API响应中的完全折扣项，返回接近零的残值，而不是0.00。
1. **ACSD-66118**：如果配置缓存未刷新，则更新存储视图代码将清除设计配置设置。
1. **ACSD-66139**：在订购期间，GraphQL为不存在的或不活动的购物车返回UNDEFINED错误。
1. **ACSD-66301**：将产品从订单移回管理员中的购物车会导致数量不匹配。
1. **ACSD-66434**：公司GraphQL查询中缺少客户ID。
1. **ACSD-66441**：分层导航在多存储设置中显示不正确的属性选项。

使用左侧的菜单导航到特定的修补程序页面。
