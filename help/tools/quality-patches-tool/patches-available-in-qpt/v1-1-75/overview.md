---
title: 概述：[!DNL Quality Patches Tool] (QPT) v1.1.75
description: 此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.75中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 5c33cd529bff9208d640cec3c4068f578a9e376c
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.75

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.75中提供的修补程序所修复的问题。

QPT v1.1.75包含以下修补程序：
1. **ACSD-68289**：修复了以下问题：如果所有可搜索字段总体满足最低匹配条件，则全文搜索现在返回匹配产品，而不是要求条件由单个字段满足。
1. **ACSD-68359**：修复了在选择具有大购物车的&#x200B;**[!UICONTROL Pick in Store]**&#x200B;时出现&#x200B;*414*&#x200B;错误。
1. **ACSD-68451**：修复了以下多个网站的问题：公司管理员登录一个网站，在另一个网站上创建不相关的公司，但错误地关联到该不相关的公司。
1. **ACSD-68517**：修复了&#x200B;**[!UICONTROL Catalog]**&#x200B;和&#x200B;**[!UICONTROL Catalog Search]**&#x200B;页面上的表单重新提交错误。
1. **ACSD-68490**：在可配置产品创建期间对受限管理员可见的&#x200B;**[!UICONTROL Add New Attribute]**&#x200B;按钮。
1. **ACSD-68573**：修复了类别权限未正确应用于客户愿望清单项目的问题。 修复后，在Web和GraphQL中均可正确显示愿望清单项目并进行分页。
1. **ACSD-68615**：修复了当处理的组合缺少订单ID时，库存预留补偿CLI显示异常的问题。
1. **ACSD-68793**：修复了在将有效产品分配给共享目录时，有效产品被错误拒绝的问题。
1. **ACSD-68925**：修复了GraphQL请求的响应现在通过HTTP规范与GraphQL保持一致的问题。 如果请求无法解析、未授权或遇到一般问题（如果请求已解析），则会返回4XX响应代码。

使用左侧的菜单导航到特定的修补程序页面。
