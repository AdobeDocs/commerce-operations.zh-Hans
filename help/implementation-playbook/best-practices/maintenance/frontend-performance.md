---
title: 审核前端绩效
description: 通过使用Web性能工具审核Adobe Commerce店面操作，识别并解决对网站性能产生负面影响的问题。
role: Admin, User, Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# 前端性能的最佳实践

使用Web性能工具检查Adobe Commerce商店的前端性能。
这些工具使用各种量度来提供强大的分析和建议，以提高您在线商店的性能。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 检查前端性能

要检查网站商店的前端性能，请执行以下操作：

1. 使用Web性能工具审核前端性能，例如：

   - **[Google灯塔](https://web.dev/measure/)**- Lighthouse对性能、辅助功能、渐进式Web应用程序、SEO等方面进行审核。 有关运营灯塔的不同方式的详细信息，请参阅 [灯塔概述](https://developer.chrome.com/docs/lighthouse/overview).)
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)**- PageSpeed Insights可快速提供有关网页性能降低的原因的详细报告以及有关如何修复该报告的建议。

1. 审核报告并实施为改进存储性能而提供的建议。

## 其他信息

- [管理员用户的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用CLI进行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [面向开发人员的索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)


