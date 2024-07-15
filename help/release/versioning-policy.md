---
title: 发布策略
description: 了解不同类型的Adobe Commerce版本，包括次要修补程序、安全修补程序、功能、修补程序、单个修补程序和自定义修补程序。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Adobe Commerce发布策略

Adobe Commerce在单个模块级别（例如`magento/framework 101.1.1`）使用[语义版本控制](https://semver.org/)，但不用于营销版本号。 例如：

- **主要版本**—2
- **次要版本** - 2.4
- **PATCH版本** - 2.4.5
   - **安全修补程序版本**—2.4.5-p1
      - 安全错误修复
      - 安全性增强
- **BETA修补程序版本**—2.4.7-beta2
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
- 在特殊情况下，可能会发布重大更改或其他修补程序或修补程序，以解决安全性或合规性问题以及影响重大的质量问题。 在模块级别，这些更改主要是PATCH级别的更改；有时是次要级别的更改。

### SECURITY补丁发行版

{{$include /help/_includes/security-patch-release-overview.md}}

## Beta补丁版本

Adobe Commerce功能正式发布前的版本已公开提供给所有Adobe Commerce客户和Adobe合作伙伴。 它留出了在正式发布之前的一段额外时间，让您可以审查代码和受影响的组件。

Beta版本可能包含缺陷，并“按原样”提供，无任何类型的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(通过Adobe支持服务或其他方式)Beta版本。 建议客户谨慎使用，并且不要以任何方式依赖Beta版本和/或任何随附文档或材料的正确功能或性能。 因此，使用Beta版本的任何行为都要由客户自行承担风险。

## 可扩展性、基础架构和服务版本

功能版本包含作为独立服务交付的新功能和功能更新，与修补程序版本不同。 示例包括API Mesh和Eventing等可扩展性技术，Product Recommendations和Live Search等SaaS产品，B2B和PWA Studio等独立模块，以及对我们的云托管服务和基础架构的更新。

## 修补程序

修补程序是包含影响许多商家的高影响安全或质量修补程序的修补程序，例如针对零日漏洞的修补程序。 Adobe会根据需要发布受关键安全或质量问题支持和影响的Adobe Commerce版本修补程序。 修补程序已发布到我们知识库的[已知问题部分](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)。 这些修复包括在下一个计划的修补程序版本中。

>[!NOTE]
>
>修补程序可能包含向后不兼容的更改。

## 单个修补程序

单个修补程序包含针对特定问题的低影响质量修复。 这些修复适用于Adobe Commerce支持的次要版本。 根据我们的[软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)，Adobe会根据需要发布Adobe Commerce的单个修补程序。

>[!NOTE]
>
>单个修补程序不包含向后不兼容的更改。

## 自定义修补程序

由非Adobe人员创建，用于修复问题或由于各种原因修改Adobe Commerce代码。 自定义修补程序通过[Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)提供。

## 相关主题

- [版本控制](https://developer.adobe.com/commerce/php/development/versioning/)
- [即将发布的版本](schedule.md)
- [软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
