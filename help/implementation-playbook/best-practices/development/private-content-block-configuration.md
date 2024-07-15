---
title: 专用内容块的最佳实践
description: 了解配置专用内容块以优化店面性能的最佳实践。
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# 专用内容块的最佳实践

当专用内容块包含`_isScopePrivate`变量时，该块无法缓存。 由于未缓存专用块，因此Adobe Commerce必须为每个客户请求检索相同的数据，这会增加服务器负载。

请创建块和模板以显示与用户无关的数据，而不是将`_isScopePrivate`变量用于私有内容。 此数据已由Adobe Commerce UI组件替换为特定于用户的数据，该组件可更高效地处理预渲染数据。 有关说明，请参阅&#x200B;_[!DNL Commerce PHP Extensions Guide]_中的[私人内容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 潜在的性能影响

如果网站具有包含`_isScopePrivate`变量的私有内容块，则会触发AJAX请求为每个客户请求检索相同的数据。 这会增加响应时间，并使用可用于处理更多业务关键型店面操作的额外资源，例如客户注册、购物车更新、订单提交和支付交易。

## 其他信息

- [私有内容](../../../performance/configuration.md#client-side-optimization-settings)
- [高吞吐量AJAX请求导致性能不佳](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
