---
title: 疑难解答最佳实践
description: 了解如何对Adobe Commerce实施问题进行故障诊断。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# 疑难解答最佳实践

请遵循这些最佳实践，以便在云基础架构问题上有效地对Adobe Commerce进行故障排除。

## 受影响的产品和版本

云基础架构上的Adobe Commerce

## 最佳实践

| 问题类型 | 最佳实践 | 资源 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 部署问题 | **遵循部署最佳实践。** 13%的支持票证涉及部署问题。 更新了最佳实践，纳入了预防其中许多原因的方法。 | [构建和部署的最佳实践](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 在我们的开发人员文档中。 |
| 站点关闭问题 | **使用站点故障排查程序。** Cron可能长时间运行，并且可能相互超越。 他们是许多中断和性能问题的源头。 | [Site Down疑难解答程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) 和 [如何重置cron作业](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 在我们的支持知识库中。 |
| 性能问题 | **如果您没有使用Adobe Commerce横幅，请禁用它。** 当启用了横幅但未使用时，资源将用于在不需要时对数据库进行查找，这将导致性能问题。 | [禁用Adobe Commerce横幅输出以提高性能](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) 在我们的支持知识库中。 |
| 搜索问题 | **Adobe Commerce 2.4.0中删除了MySQL目录搜索引擎。** 在安装版本2.4.0之前，必须设置并配置Elasticsearch主机。请参阅我们的开发人员文档中的安装和配置Elasticsearch。 | [设置Elasticsearch服务](https://devdocs.magento.com/cloud/project/services-elastic.html) 在我们的开发人员文档中。 |
| 自定义错误 | **请勿在高峰期部署。** 添加和删除用户将触发部署。 | [零停机部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) 在我们的开发人员文档中。 |
| 数据库错误和问题 | **数据库问题导致部署（挂接后问题）、性能和站点关闭情况。** 许多事件涉及错误或数据库空间分配不足。 | [MariaDB错误代码](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes)； [管理存储空间](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （包括数据库）。 |
| 配置问题 | **按计划编制索引，而不是在保存时编制索引。** 这是最有效的索引配置。 “保存”上的索引将导致完全重新索引。 | [配置索引器](../../../configuration/cli/manage-indexers.md#configure-indexers) 在我们的开发人员文档中。 |
| 自定义代码问题 | **检查您的慢速查询日志，以查看是否有机会识别并可能会终止需要太多时间才能完成的流程。** 查询速度慢可能会导致数据库死锁，从而导致站点故障和性能问题。 | [在MySQL中检查缓慢的查询和进程耗时过长](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 扩展问题 | **仅使用Commerce Marketplace上当前已验证的扩展。** | [Adobe Commerce的扩展](https://marketplace.magento.com/extensions.html) |
| 资源问题 | **监视可用内存和空间，并优化存储。** 在执行占用大量资源（例如，部署）的操作之前，您可能具有可用空间。 文件存储优化不当（例如，过大且内容丰富的图像）也会导致空间不足。 资源不足会导致性能问题、站点关闭、部署停滞和部署失败。 | [管理磁盘空间](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （在我们的开发人员文档中）； [文件存储不足/已耗尽，特定页面加载缓慢](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) 在我们的支持知识库中。 |
