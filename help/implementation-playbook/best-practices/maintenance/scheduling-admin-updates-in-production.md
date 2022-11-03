---
title: 在生产站点上计划管理员更新
description: 了解计划对Adobe Commerce进行关键更新以防止性能缓慢和中断的最佳实践。
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# 在生产站点上计划管理员更新的最佳实践

安排在非高峰时间对Adobe Commerce站点进行关键更新和操作，以防止生产站点的性能缓慢和停机。

关键操作示例：

- 管理员配置更改，例如更新产品属性或将产品子类别移动到其他类别
- 数据导入或导出操作

关键操作会导致缓存失效和重新索引操作，这会显着增加响应时间，从而可能导致站点停机。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 其他信息

- [缓存的最佳实践](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [专用内容：使私有内容失效](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [硬件建议：缓存](../../../performance/hardware.md#caches)
- [高级设置：设置Redis](../../../performance/advanced-setup.md#set-up-redis)

