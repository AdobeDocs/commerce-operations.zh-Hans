---
title: 专用内容块的最佳实践
description: 了解配置专用内容块以优化店面性能的最佳实践。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# 专用内容块的最佳实践

当专用内容块包含 `_isScopePrivate` 变量中，无法缓存块。 由于私有块未缓存，因此Adobe Commerce必须为每个客户请求检索相同的数据，这会增加服务器负载。

而不是使用 `_isScopePrivate` 变量，请创建块和模板以显示与用户无关的数据。 此数据由Adobe Commerce UI组件替换为用户特定的数据，该组件可更高效地处理预渲染数据。 有关说明，请参阅 [专用内容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) 在 _[!DNL Commerce PHP Extensions Guide]_.

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 潜在的性能影响

具有包含 `_isScopePrivate` 变量会触发AJAX请求，以检索每个客户请求的相同数据。 这会增加响应时间，并使用可用于处理更多业务关键型店面操作（如客户注册、购物车更新、订单提交和付款交易）的额外资源。

## 其他信息

- [专用内容](../../../performance/configuration.md#client-side-optimization-settings)
- [高吞吐量AJAX请求导致性能不佳](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


