---
title: 结论
description: 重新访问“按规模交付商务体验”指南中的概念。
exl-id: a5d5c398-451f-4283-b787-d16c7486e824
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# 结论

本内容旨在作为一个高级指南，在准备AEM/CIF/Adobe Commerce环境以应对大量负载时，提供一些需要初步调查的方面。 Adobe Commerce、CIF和Fast的许多方面都未包含在上述指南中，因此需要针对您的环境进行特定的优化。 此外，自定义代码和第三方模块可能会对响应时间产生影响，这些响应时间在此处无法涵盖。

为了降低引入的更改或代码对AEM/CIF/Adobe Commerce最终用户响应时间造成负面影响的风险，应确保实施全面且可重复的性能测试策略，包括定义可随时间测量的KPI。 性能测试不仅应在上线之前执行，而且应在上线后继续执行，最好是在每个主要版本或生产环境更改之前执行，以衡量任何性能影响。
