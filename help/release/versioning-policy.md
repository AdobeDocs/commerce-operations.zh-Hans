---
title: 发布策略
description: 了解不同类型的Adobe Commerce版本。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: f7b22089bcf88f6c881b0cbd4d7f77d795d9071b
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# Adobe Commerce发布策略

Adobe Commerce在单个模块级别（例如[）使用](https://semver.org/)语义版本控制`magento/framework 101.1.1`，但不用于营销版本号。 例如：

- **主要版本**—2
- **次要版本** - 2.4
- **PATCH版本** - 2.4.8
   - **安全修补程序版本**—2.4.8-p1
      - 安全错误修复
      - 安全性增强
- **ALPHA修补程序版本**—2.4.8-alpha1
- **BETA修补程序版本**—2.4.8-beta1
- **可扩展性、基础架构和服务版本**
- **修补程序**
- **单个修补程序**
- **自定义修补程序**

## 次要版本

以下准则适用于次要版本：

- 可以进行重大更改；为Adobe Commerce 2.2.x编写的代码可能无法再用于Adobe Commerce 2.3.x。例如，次要版本可能会引入对主要系统要求和依赖项（如PHP）的支持。
- 模块版本可能有所不同。 例如，一些模块更改是在新补丁中引入的，而其他模块更改是在次要版本中引入的。
- 次要版本可能包括一些新功能，在升级期间您可能需要或您的解决方案合作伙伴进行额外的操作以确保兼容性。
- 次要版本可能包括对安全和质量问题的修复。

## PATCH版本

补丁发行主要侧重于提供安全性、性能、合规性和高优先级的质量修复，帮助您保持网站在最高峰运行。

以下准则适用于修补程序版本：

- 最新支持的次要版本将获得完整的功能质量修复和增强功能。
- 避免进行可能破坏扩展或代码兼容性的更改。 例如，为版本2.2.0编写的代码在版本2.2.7上仍然有效。
- 在特殊情况下，可能会发布重大更改或其他修补程序或修补程序，以解决安全性或合规性问题以及影响重大的质量问题。 在模块级别，这些更改主要是PATCH级别更改，有时是次要级别更改。

### SECURITY补丁发行版

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Alpha补丁版本

Adobe Commerce功能的Beta前版本已公开提供给所有Adobe Commerce客户和Adobe合作伙伴。 Alpha版本旨在对仍在积极开发的功能提供早期反馈和评估。 这些版本提供了在Beta和General Availability版本之前提前测试和集成规划的机会。

Alpha版本可能不完整，并且可能包含缺陷。 它们按“原样”提供，不提供任何形式的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(通过Adobe支持服务或其他方式)Alpha版本。 客户不应依赖Alpha版本或任何随附文档或材料的正确功能或性能。 使用Alpha版本完全由客户自行承担风险。

## Beta补丁版本

Adobe Commerce功能的正式发布之前版本已公开提供给所有Adobe Commerce客户和Adobe合作伙伴。 它留出了在正式发布之前的一段额外时间，让您可以审查代码和受影响的组件。

Beta版本可能包含缺陷，并“按原样”提供，无任何类型的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(通过Adobe支持服务或其他方式)Beta版本。 客户不应依赖Beta版本或任何随附文档或材料的正确功能或性能。 因此，使用Beta版本的任何行为都要由客户自行承担风险。

## 功能、云基础架构和可扩展性版本

云基础架构和功能版本包含作为独立服务（与修补程序版本不同）提供的新功能和功能更新。 示例包括但不限于：

- 云托管服务和基础设施的更新
- B2B
- SaaS产品（“目录服务”、“数据连接”、“产品推荐”和“实时搜索”）
- 可扩展性技术(管理UI SDK、API Mesh、App Builder Starter Kit、Eventing和Webhooks)

## 修补程序

修补程序是包含影响许多商家的高影响安全或质量修补程序的修补程序，例如针对零日漏洞的修补程序。 当严重的安全或质量问题影响受支持的Adobe Commerce版本时，Adobe会根据需要发布这些版本的修补程序。 修补程序已发布到知识库的[已知问题部分](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)。 这些修复包括在下一个计划的修补程序版本中。

>[!NOTE]
>
>修补程序可能包含与向后不兼容的更改。

## 单个修补程序

单个修补程序包含针对特定问题的低影响质量修复。 这些修复适用于Adobe Commerce支持的次要版本。 根据[软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)，Adobe会根据需要发布Adobe Commerce的单个修补程序。

>[!NOTE]
>
>单个修补程序不包含向后不兼容的更改。

## 隔离的修补程序

独立修补程序是独立于完整安全修补程序发布的安全修补程序，用于实现更快的实施。 每个独立的修补程序都会解决特定的安全问题，并且都包含在最新或即将推出的完整安全修补程序中。 有关该问题的详细信息在相关安全公告中提供，该公告链接到知识库(KB)文章，其中包含修补程序详细信息、如何应用修补程序以及其他信息。

请参阅[安全中心](https://helpx.adobe.com/security/products/magento.html)以查找Adobe Commerce的最新安全更新。

## 自定义修补程序

由非Adobe人员创建，用于修复问题或由于各种原因修改Adobe Commerce代码。 自定义修补程序通过[Quality Patches Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)提供。
