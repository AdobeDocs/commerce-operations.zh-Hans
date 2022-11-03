---
title: 配置站点、商店和商店视图的最佳实践
description: 了解配置网站、商店和商店视图以最大化网站性能的最佳实践。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# 配置站点、商店和商店视图的最佳实践

为获得最佳站点性能，在云基础架构项目上为Adobe Commerce最多配置50个站点、50个商店和50个商店视图。

>[!NOTE]
>
>对于云基础架构上的Adobe Commerce，最佳实践专门适用于生产环境（可能适用于受资源限制的专业架构上的暂存环境），该环境的资源会多于集成和开发环境。 对于集成（专业和入门）和暂存环境（入门），请将商店查看次数减少到5次或10次以下（需经过技术审查）。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 提高绩效的战略

如果您的项目需要许多网站、商店或商店视图，则可以使用以下策略来提高性能：

- 通过将逻辑转换为类别来重构目录
- 使用外部价格和价格管理系统(PMS)将价目表与目录数据分开。
- 使用替代的noSQL数据存储，如Elasticsearch

## 潜在的性能影响

网站和存储是目录数据的乘数，因此拥有多个网站和存储可能会在以下方面对网站性能产生负面影响：

- 较大的索引表可增加完成索引操作所需的时间 [价格指数].
- 增加的检索应用程序配置时间会降低非缓存目录页面的前端响应时间。
- 由于每个网站单独保存数据，因此在管理员中完成保存操作所需的时间会显着增加。


## 其他信息

- [了解网站、商店和商店视图](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [设置多个网站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

