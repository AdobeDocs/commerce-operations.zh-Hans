---
title: 静态内容部署最佳实践
description: 了解如何避免静态内容未出现在Adobe Commerce店面中的问题。
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 静态内容部署最佳实践

本文介绍了Adobe Commerce中的静态内容部署(SCD)最佳实践，以帮助避免静态内容在您的网站上不可用的问题。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

* 云基础架构上的Adobe Commerce
* Adobe Commerce内部部署

## 最佳实践

要避免静态内容在网站上不可用的问题，请按照以下最佳实践操作，确保您的静态内容已正确配置和部署：

1. 请确保遵循部署准则：
   * 有关Adobe Commerce内部部署（所有版本），请参阅 [部署概述](../../../configuration/deployment/overview.md) 在我们的开发人员文档中。
   * 有关云基础架构上的Adobe Commerce（所有版本），请参阅 [云部署过程](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) 和 [静态内容部署策略](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) 在我们的开发人员文档中。

1. 对于云基础架构上的Adobe Commerce（所有版本），请确保ece-tools使用的是最新版本。 请参阅： [更新ece-tools版本](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 在我们的开发人员文档中。
1. 对于云基础架构上的Adobe Commerce（所有版本），请确保在构建阶段而不是部署阶段部署静态内容。 请参阅： [存储设置的配置管理 — 静态内容部署性能](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) 在我们的开发人员文档中。
1. 确保没有长时间运行的cron作业，并终止任何长时间运行的cron进程。 长时间运行的cron作业可能会占用CPU资源，并可能大大增加部署时间。
1. 对于本地Adobe Commerce（所有版本），请检查 `php` CLI中的进程可以访问 `pub/static` 目录。 否则，您可能会遇到静态内容部署无法将文件写入该目录的问题。 有关更多信息： [文件系统访问权限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) 在我们的开发人员文档中。
1. 确保 `generated` 目录不是跨内部版本的共享目录；否则，内部版本可能会随机失败。 有关更多信息：
   * Adobe Commerce内部部署（所有版本）： [技术详细信息](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) 在我们的开发人员文档中。
   * 云基础架构上的Adobe Commerce（所有版本）： [部署过程 — 阶段2：构建](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) 在我们的开发人员文档中。

1. 检查您的SCD策略。 此 *快速* 策略是默认选项。 有关更多信息：
   * Adobe Commerce内部部署（所有版本）： [静态文件部署策略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) 在我们的开发人员文档中。
   * 云基础架构上的Adobe Commerce（所有版本）： [部署变量 — SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) 在我们的开发人员文档中。

## 其他信息

在我们的开发人员文档中：

* [静态内容容器](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [静态内容签名](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [部署变量 — STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [部署流程](../../../performance/deployment-flow.md)
* [零停机部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [优化云部署](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
