---
title: 配置站点、商店和存储视图的最佳实践
description: 了解配置站点、商店和存储视图以最大限度地提高站点性能的最佳实践。
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: a81e88a4293880ae90cd531ce60c5a2b177188f2
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# 配置站点、商店和存储视图的最佳实践

对于云基础架构上的Adobe Commerce，最佳实践特别适用于生产环境（并可能适用于专业架构上的暂存，取决于资源限制），生产环境将比集成和开发环境拥有更多资源。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 提高性能的策略

如果您的项目需要许多网站、商店或商店视图，则可以使用以下策略来提高性能：

- 通过将逻辑移动到类别来重构目录
- 使用外部价格和价格管理系统(PMS)将价目表与目录数据分开。
- 使用替代noSQL数据存储，如Elasticsearch

## 潜在的性能影响

网站和商店是目录数据的倍数，因此拥有多个网站和商店可能会以下列方式负面影响网站性能：

- 索引表越大，完成索引操作[价格索引]所需的时间就越长。
- 检索应用程序配置的时间增加会降低非缓存目录页面的店面响应时间。
- 显着增加了在管理员中完成保存操作所需的时间，因为每个网站的数据都单独保存。


## 其他信息

- [了解网站、商店和商店视图](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [设置多个网站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
