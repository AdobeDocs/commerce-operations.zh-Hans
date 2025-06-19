---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.52
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.52中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: e6fc655e-0809-4b47-8be1-1fc36ae30753
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.52

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.52中提供的修补程序所修复的问题。

QPT v1.1.52包含以下修补程序：

1. **ACSD-59366**：修复了在删除团队时出现错误的问题，该团队包含未在团队列表中显示的已停用用户。
1. **ACSD-59865**：修复了购物车中的产品数量不足以应用规则时，[!UICONTROL Cart Price Rule]无法取消以前应用的规则的问题。
1. **ACSD-59925**：修复了GraphQL中按位置对媒体集中的项目进行排序的问题。
1. **ACSD-59952**：修复了在使用分配给现有共享目录的组ID创建共享目录时出现错误的问题。
1. **ACSD-60590**：提高了为大量下单订单生成&#x200B;*[!UICONTROL Bestsellers Aggregated Daily Reports]*&#x200B;的性能。
1. **ACSD-60673**：修复了结账时多个付款方法的[!UICONTROL Cart Price Rule]未正确应用于特定付款方法的问题。
1. **ACSD-60684**：修复了按多个字段排序的GraphQL产品无法按预期工作的问题。
1. **ACSD-60788**：修复了由于内容安全策略(CSP)错误而无法执行[!DNL Google Tag Manager]的自定义脚本的问题。
1. **ACSD-61322**：修复了未分配给默认（常规组）的[!UICONTROL Shared Catalog]的产品/类别仍包含在XML Sitemap中的问题。
1. **ACSD-61366**：修复了在为DB连接指定端口时，必须在主机参数&#x200B;*中配置*&#x200B;端口的情况下运行`setup:static-content:deploy --jobs 4`命令且多个作业失败的问题。

使用左侧的菜单导航到特定的修补程序页面。
