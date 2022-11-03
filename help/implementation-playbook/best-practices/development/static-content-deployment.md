---
title: 静态内容部署最佳实践
description: 了解如何避免静态内容未在Adobe Commerce或Magento Open Source店面中显示的问题。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# 静态内容部署最佳实践

本文介绍了静态内容部署(SCD)在Adobe Commerce中的最佳实践，以帮助避免静态内容在您的网站上不可用的问题。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

* Adobe Commerce云基础架构
* Adobe Commerce内部
* Magento Open Source

## 最佳实践

要避免静态内容在您的网站上不可用的问题，请按照以下最佳实践操作，以确保您的静态内容已正确配置和部署：

1. 确保遵循部署准则：
   * 有关Adobe Commerce内部部署和Magento Open Source（所有版本），请参阅 [部署概述](../../../configuration/deployment/overview.md) ，请参阅我们的开发人员文档。
   * 有关云基础架构上的Adobe Commerce（所有版本），请参阅 [云部署流程](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) 和 [静态内容部署策略](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) ，请参阅我们的开发人员文档。

1. 对于云基础架构上的Adobe Commerce（所有版本），请确保ece-tools位于最新版本上。 请参阅： [更新ece-tools版本](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) ，请参阅我们的开发人员文档。
1. 对于云基础架构上的Adobe Commerce（所有版本），请确保在构建阶段而不是部署阶段部署静态内容。 请参阅： [存储设置的配置管理 — 静态内容部署性能](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) ，请参阅我们的开发人员文档。
1. 请确保您没有长时间运行的cron作业，并停止任何长时间运行的cron进程。 长时间运行的cron作业可能占用CPU资源，并且可能会大大增加部署时间。
1. 对于Adobe Commerce内部部署版和Magento Open Source版（所有版本），请检查 `php` 进程在CLI中具有访问 `pub/static` 目录访问Advertising Cloud的帮助。 否则，您可能会遇到静态内容部署无法将文件写入该目录的问题。 有关更多信息： [文件系统访问权限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) ，请参阅我们的开发人员文档。
1. 确保 `generated` 目录不是内部版本之间的共享目录；否则，生成可能会随机失败。 有关更多信息：
   * Adobe Commerce本地和Magento Open Source（所有版本）： [技术详细信息](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) ，请参阅我们的开发人员文档。
   * 云基础架构上的Adobe Commerce（所有版本）： [部署流程 — 第2阶段：构建](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) ，请参阅我们的开发人员文档。

1. 检查您的SCD策略。 的 *快速* 策略是默认设置。 有关更多信息：
   * Adobe Commerce本地和Magento Open Source（所有版本）： [静态文件部署策略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) ，请参阅我们的开发人员文档。
   * 云基础架构上的Adobe Commerce（所有版本）： [部署变量 — SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) ，请参阅我们的开发人员文档。

## 其他信息

在我们的开发人员文档中：

* [静态内容容器](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [静态内容签名](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [部署变量 — STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [部署流程](../../../performance/deployment-flow.md)
* [零停机部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [优化云部署](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

