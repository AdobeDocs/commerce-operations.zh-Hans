---
title: 疑难解答最佳实践
description: 了解如何对Adobe Commerce实施问题进行故障诊断。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 疑难解答最佳实践

请遵循这些最佳实践，以便在云基础架构问题上有效地对Adobe Commerce进行故障排除。

## 受影响的产品和版本

云基础架构上的Adobe Commerce

## 最佳实践

| 问题类型 | 最佳实践 | 资源 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 部署问题 | **遵循部署最佳实践。** 13%的支持票证涉及部署问题。 更新了最佳实践，纳入了预防其中许多原因的方法。 | 在开发人员文档中[生成和部署的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices)。 |
| 站点关闭问题 | **使用站点故障排查程序。** Cron可能长时间运行并且可能相互超载。 他们是许多中断和性能问题的源头。 | [Site Down Troubleshooter](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=zh-Hans)和[如何在我们的支持知识库中重置cron作业](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=zh-Hans)。 |
| 性能问题 | **如果您未使用Adobe Commerce横幅，请将其禁用。**&#x200B;当启用了横幅但未使用时，资源将用于在不需要时对数据库进行查找，这将导致性能问题。 | [禁用Adobe Commerce横幅输出以提高我们的支持知识库中的性能](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html?lang=zh-Hans)。 |
| 搜索问题 | **Adobe Commerce 2.4.0中已删除MySQL目录搜索引擎。**&#x200B;您必须先设置并配置Elasticsearch主机，然后才能安装版本2.4.0。请参阅我们的开发人员文档中的安装和配置Elasticsearch。 | 在开发人员文档中[设置Elasticsearch服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。 |
| 自定义错误 | **请勿在高峰期部署。**&#x200B;添加和删除用户将触发部署。 | 在开发人员文档中[零停机部署](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)。 |
| 数据库错误和问题 | **数据库问题导致部署（挂接后问题）、性能和站点关闭情况。**&#x200B;许多涉及错误或数据库空间分配不足。 | [MariaDB错误代码](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes)；[管理存储空间](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)（包括数据库），位于我们的开发人员文档中。 |
| 配置问题 | **按计划编制索引，而不是在保存时编制索引。**&#x200B;这是最有效的索引配置。 “保存”上的索引将导致完全重新索引。 | 在开发人员文档中[配置索引器](../../../configuration/cli/manage-indexers.md#configure-indexers)。 |
| 自定义代码问题 | **检查您的慢速查询日志，查找机会以识别并可能会终止需要太多时间才能完成的进程。**&#x200B;查询速度慢可能导致数据库死锁，从而导致站点故障和性能问题。 | [在MySQL中检查慢查询和进程花费太长时间](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html?lang=zh-Hans) |
| 扩展问题 | **仅使用Commerce Marketplace上当前已验证的扩展。** | Adobe Commerce的[扩展](https://marketplace.magento.com/extensions.html) |
| 资源问题 | **监视可用内存和空间，并优化存储。**&#x200B;在执行占用大量资源的操作（例如部署）之前，您可能具有可用空间。 文件存储优化不当（例如，过大且内容丰富的图像）也会导致空间不足。 资源不足会导致性能问题、站点关闭、部署停滞和部署失败。 | [在我们的开发人员文档中管理磁盘空间](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)；[文件存储不足/已用尽，特定页面加载缓慢](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=zh-Hans)在我们的支持知识库中。 |
