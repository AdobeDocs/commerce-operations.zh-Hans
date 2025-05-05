---
title: 审核前端性能
description: 通过使用Web性能工具审核Adobe Commerce店面操作，发现并解决对网站性能产生负面影响的问题。
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 1%

---

# 前端性能最佳实践

使用Web性能工具检查Adobe Commerce存储的前端性能。
这些工具使用各种量度提供强大的见解和建议以提高在线商店的性能。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 检查前端性能

要检查网站商店的前端性能，请执行以下操作：

1. 使用Web性能工具审核前端性能，例如：

   - **[Google Lighthouse](https://web.dev/measure/)** - Lighthouse对性能、可访问性、渐进式Web应用程序、SEO等进行了审核。 有关运行灯塔的不同方法的详细信息，请参阅[灯塔概述](https://developer.chrome.com/docs/lighthouse/overview)。
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)**—PageSpeed Insights可快速提交有关网页性能缓慢原因的详细报告以及修复建议。

1. 审查审计报告，落实为改善商店业绩而提出的建议。

## 其他信息

- [管理员用户的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用CLI进行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=zh-Hans)
- [针对开发人员的索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
