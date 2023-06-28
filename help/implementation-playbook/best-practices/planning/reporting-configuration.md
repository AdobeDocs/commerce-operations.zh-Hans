---
title: 报表配置最佳实践
description: 如果不使用报表模块，请通过删除报表模块来优化网站性能。
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# 报告配置最佳实践

如果您的业务不需要报告或动态客户区段功能，请禁用 [报表功能](https://docs.magento.com/user-guide/configuration/general/reports.html) 以提高存储性能。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 禁用报告

如果您不使用报表或动态客户区段，请禁用报表功能。

1. 在管理员中，导航到 **商店** > **设置** > **配置** > **常规** > **报告**.
1. 下 **常规选项**，设置 **启用报表** 到 *否*.
1. 通过运行刷新缓存 `php bin/magento cache:flush` 或在“管理员”中的 **系统** > **工具** > **缓存管理**.

## 其他信息

- [在Adobe Commerce中生成报表](https://docs.magento.com/user-guide/reports.html)
- [客户动态区段](https://docs.magento.com/user-guide/marketing/customer-segments.html)
