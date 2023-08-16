---
title: 正在安排生产站点上的管理员更新
description: 了解为Adobe Commerce安排关键更新以防止性能缓慢和出现中断的最佳实践。
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# 在生产网站上计划管理员更新的最佳实践

在非高峰时间安排Adobe Commerce网站上的关键更新和操作，以防止生产网站性能变慢和出现中断。

关键操作示例：

- 管理员配置更改，例如更新产品属性，或将产品子类别移动到另一个类别
- 数据导入或导出操作

关键操作会导致缓存失效和重新索引操作，这些操作会显着增加响应时间，从而可能导致站点中断。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 其他信息

- [缓存最佳实践](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [私有内容：使私有内容无效](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [硬件建议：缓存](../../../performance/hardware.md#caches)
- [高级设置：设置Redis](../../../performance/advanced-setup.md#set-up-redis)
