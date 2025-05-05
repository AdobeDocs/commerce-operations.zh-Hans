---
title: 静态内容部署最佳实践
description: 了解如何避免静态内容未出现在Adobe Commerce店面中的问题。
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 静态内容部署最佳实践

本文介绍了Adobe Commerce中的静态内容部署(SCD)最佳实践，以帮助避免静态内容在您的网站上不可用的问题。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

* 云基础架构上的Adobe Commerce
* Adobe Commerce内部部署

## 最佳实践

要避免静态内容在网站上不可用的问题，请按照以下最佳实践操作，确保您的静态内容已正确配置和部署：

1. 请确保遵循部署准则：
   * 对于本地Adobe Commerce（所有版本），请参阅我们的开发人员文档中的[部署概述](../../../configuration/deployment/overview.md)。
   * 有关云基础架构上的Adobe Commerce（所有版本），请参阅我们的开发人员文档中的[云部署流程](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/process)和[静态内容部署策略](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/static-content)。

1. 对于云基础架构上的Adobe Commerce（所有版本），请确保ece-tools使用的是最新版本。 请参阅我们的开发人员文档中的[更新ece-tools版本](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package)。
1. 对于云基础架构上的Adobe Commerce（所有版本），请确保在构建阶段而不是部署阶段部署静态内容。 请参阅我们的开发人员文档中的[存储设置的配置管理 — 静态内容部署性能](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over)。
1. 确保没有长时间运行的cron作业，并终止任何长时间运行的cron进程。 长时间运行的cron作业可能会占用CPU资源，并可能大大增加部署时间。
1. 对于Adobe Commerce内部部署（所有版本），请检查CLI中的`php`进程是否有权访问`pub/static`目录。 否则，您可能会遇到静态内容部署无法将文件写入该目录的问题。 有关详细信息：[文件系统访问权限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=zh-Hans)（位于我们的开发人员文档中）。
1. 确保`generated`目录不是跨内部版本的共享目录；否则，内部版本可能会随机失败。 有关更多信息：
   * Adobe Commerce内部部署（所有版本）：我们的开发人员文档中的[技术详细信息](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=zh-Hans)。
   * 云基础架构上的Adobe Commerce（所有版本）：[部署流程 — 阶段2：开发人员文档中的内部版本](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build)。

1. 检查您的SCD策略。 *quick*&#x200B;策略是默认策略。 有关更多信息：
   * Adobe Commerce内部部署（所有版本）：开发人员文档中的[静态文件部署策略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html?lang=zh-Hans)。
   * 在开发人员文档中，查看云基础架构上的Adobe Commerce（所有版本）： [部署变量 — SCD\_STRATEGY](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy)。

## 其他信息

在我们的开发人员文档中：

* [静态内容容器](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [静态内容签名](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html?lang=zh-Hans)
* [部署变量 — STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [部署流程](../../../performance/deployment-flow.md)
* [零停机部署](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [优化云部署](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
