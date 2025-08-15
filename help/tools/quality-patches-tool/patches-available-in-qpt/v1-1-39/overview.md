---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.39
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.39中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.39

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.39中提供的修补程序所修复的问题。

QPT v1.1.39包含以下修补程序：

1. **ACSD-53704**：修复了在奖励点过期后错误计算奖励点余额历史记录的问题。
1. **ACSD-53583**：改进了&#x200B;*类别产品*&#x200B;和&#x200B;*产品类别*&#x200B;索引器的部分重新索引性能。
1. **ACSD-54026**：针对非授权用户，修复了`updateCompanyRole` GraphQL请求的不正确错误消息。
1. **ACSD-54106**：修复了按名称对土耳其语重音字符进行类别产品排序不正确的问题。
1. **ACSD-52219**：修复了在书签视图之间频繁切换时，管理员网格保存的过滤器无法按预期工作的问题。
1. **ACSD-54342**：修复了不正确的错误消息&#x200B;*数据结构中的错误：导入没有有效数据的CSV文件时，值会混合*。
1. **ACSD-54660**：添加了新的输入属性&#x200B;*sort*，以便按`sort_field`和`sort_direction`对GraphQL中的客户订单进行排序。
1. **ACSD-54776**：修复了为第二个网站、商店和商店视图保存未选中&#x200B;*[!UICONTROL Use Default Value]*&#x200B;和非默认产品字段值的问题。
1. **ACSD-53998**：修复了从客户帐户注销后，基于&#x200B;**[!UICONTROL Dynamic Block]**&#x200B;的&#x200B;**[!UICONTROL Customer Segment]**&#x200B;无法正常工作的问题。
1. **ACSD-53204**：修复&#x200B;*无法保存产品。使用*&#x200B;端点向产品库添加图像的并发请求时出现`rest/V1/products/<sku>/media`错误。
1. **ACSD-47657**：添加了AWS凭据的缓存机制。 凭据提供程序现在使用Magento缓存来缓存从AWS检索到的凭据以进行EC2配置。

使用左侧的菜单导航到特定的修补程序页面。
