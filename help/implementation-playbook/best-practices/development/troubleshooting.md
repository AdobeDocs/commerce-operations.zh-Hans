---
title: 疑难解答最佳实践
description: 了解如何对Adobe Commerce实施问题进行故障诊断。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 754051c98d2c5265398f1f0806cb34128fe03c36
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# 疑难解答最佳实践

请遵循以下最佳实践，对Adobe Commerce云基础架构问题进行有效故障诊断。

## 受影响的产品和版本

Adobe Commerce云基础架构

## 最佳实践

| 问题类型 | 最佳实践 | 资源 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 部署问题 | **遵循部署最佳实践。** 13%的支持票证涉及部署问题。 最佳实践已更新，其中包括防止其中许多原因的方法。 | [构建和部署的最佳实践](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) ，请参阅我们的开发人员文档。 |
| 网站关闭问题 | **使用“Site Down（站点关闭）” “Troubleshooter（疑难解答）”。** Cron可能会长时间运行，并且会相互溢出。 它们是许多中断和性能问题的根源。 | [站点关闭疑难解答](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) 和 [如何重置cron作业](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 在我们的支持知识库中。 |
| 性能问题 | **如果您没有使用Adobe Commerce横幅，请将其禁用。** 在启用但未使用横幅时，会使用资源在不需要时对数据库进行查找，这将导致性能问题。 | [禁用Adobe Commerce横幅输出以提高性能](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) 在我们的支持知识库中。 |
| 搜索问题 | **MySQL目录搜索引擎已在Adobe Commerce 2.4.0中删除。** 在安装版本2.4.0之前，您必须安装并配置Elasticsearch主机。请参阅我们的开发人员文档中的安装和配置Elasticsearch。 | [设置Elasticsearch服务](https://devdocs.magento.com/cloud/project/services-elastic.html) ，请参阅我们的开发人员文档。 |
| 自定义错误 | **在高峰时段请勿部署。** 添加和删除用户将触发部署。 | [零停机部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) ，请参阅我们的开发人员文档。 |
| 数据库错误和问题 | **数据库问题导致部署（挂接后问题）、性能和站点关闭情况。** 许多问题涉及错误或数据库空间分配不足。 | [MariaDB错误代码](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [管理存储空间](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （包括数据库）。 |
| 配置问题 | **在保存时按计划而不是索引进行索引。** 这是最有效的索引配置。 保存时的索引将导致完全重新索引。 | [配置索引器](../../../configuration/cli/manage-indexers.md#configure-indexers) ，请参阅我们的开发人员文档。 |
| 自定义代码问题 | **检查您缓慢的查询日志，以发现确定流程的机会，并可能终止需要过多时间才能完成的流程。** 缓慢的查询可能会导致数据库死锁，从而导致站点停机和性能问题。 | [在MySQL中检查缓慢的查询和进程需要过长的时间](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 扩展问题 | **仅在Commerce Marketplace上当前使用已验证的扩展。** | [Adobe Commerce扩展](https://marketplace.magento.com/extensions.html) |
| 资源问题 | **监控可用内存和空间并优化存储。** 在执行占用大量资源的操作（例如，部署）之前，您可能会拥有可用空间。 文件存储优化不佳（例如，过大的富图像）也会导致空间不足。 资源不足会导致性能问题、站点停机、部署卡住和部署失败。 | [管理磁盘空间](https://devdocs.magento.com/cloud/project/manage-disk-space.html) 在我们的开发人员文档中； [文件存储容量低/用尽，特定页面加载速度缓慢](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) 在我们的支持知识库中。 |
