---
title: 结论
description: 重新访问大规模交付Commerce体验指南中的概念。
exl-id: a5d5c398-451f-4283-b787-d16c7486e824
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# 结论

本内容旨在作为高级指南，在准备AEM/CIF/Adobe Commerce环境以应对重负载时提供一些要初步调查的区域。 上述指南未涵盖Adobe Commerce、CIF和Fastly的许多领域，因此需要针对您的环境进行优化。 此外，自定义代码和第三方模块可能会影响响应时间，此处未涵盖这些影响。

为了降低引入会对AEM/CIF/Adobe Commerce最终用户响应时间产生负面影响的更改或代码的风险，应确保实施全面且可重复的性能测试策略，包括定义可随时间测量的KPI。 性能测试不仅应在上线之前执行，还应在上线后继续，最好是在每个主要版本发布或生产环境更改之前执行，以衡量任何性能影响。
