---
title: 报表配置的最佳实践
description: 如果您没有使用报表模块，请通过删除该模块来优化网站性能。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# 报表配置的最佳实践

如果您的企业不需要报告或动态客户区段功能，请禁用 [报表功能](https://docs.magento.com/user-guide/configuration/general/reports.html) 以提高存储性能。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 禁用报告

如果不使用报表或动态客户区段，请禁用报表功能。

1. 在管理员中，导航到 **商店** > **设置** > **配置** > **常规** > **报表**.
1. 在 **常规选项**，设置 **启用报表** to *否*.
1. 通过运行刷新缓存 `php bin/magento cache:flush` 或 **系统** > **工具** > **缓存管理**.

## 其他信息

- [在Adobe Commerce中生成报表](https://docs.magento.com/user-guide/reports.html)
- [客户动态区段](https://docs.magento.com/user-guide/marketing/customer-segments.html)
