---
title: 创建数据迁移计划
description: 按照以下步骤创建数据迁移计划，以确保成功从Magento1升级到Magento2。
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# 创建数据迁移计划

要成功迁移并避免出现问题，您需要彻底规划和测试迁移。

## 开始之前：请考虑升级

迁移是进行重大更改并为您的站点做好下一级别增长的准备的绝佳时机。 考虑您的新站点是需要设计更多的硬件，还是需要设计更高级的拓扑结构，以及更好的缓存层。

## 步骤1：查看当前网站上的扩展

* 您安装了哪些扩展？

* 您是否确定新网站上是否需要所有这些扩展？ 可能有可以安全移除的旧项目。

* 是否确定扩展是否存在Magento2版本？ 请访问[Commerce Marketplace]以查找最新版本，或与扩展提供商联系。

* 您要迁移扩展中的哪些数据库资产？

## 步骤2：构建并准备存储以进行迁移

* 使用至少与现有Magento1系统相匹配的拓扑和设计来设置Magento2硬件系统

* 在符合[Magento要求](../../installation/system-requirements.md)的系统上安装System 2.x（此版本的所有模块）和[!DNL Data Migration Tool]

* 对[!DNL Data Migration Tool]代码进行自定义调整，以防您不需要迁移某些数据（如CMS Pages、Sales Rules），或者在迁移期间希望转换Magento自定义。 阅读[!DNL Data Migration Tool]的[技术规范](technical-specification.md)以更好地了解如何从内部进行迁移

## 步骤3：练习

在生产环境中开始迁移之前，最好在测试环境中完成所有迁移步骤。

在此类迁移测试中，请执行以下步骤：

* 将Magento1存储复制到暂存服务器

* 将复制的Magento1存储完全迁移到Magento2

* 彻底测试您的新商店

## 步骤4：开始迁移

1. 确保[!DNL Data Migration Tool]具有连接到Magento1和Magento2数据库的网络访问权限。 在防火墙中打开相应的端口。

1. 停止Magento1.x管理面板中的所有活动（订单管理除外），例如发运、创建发票和贷项通知单。 可以通过调整[!DNL Data Migration Tool]中Delta模式的设置来扩展允许的活动列表。

   >[!NOTE]
   >
   >在Magento2应用商店上线之前，不得恢复这些活动。

1. 我们建议停止所有Magento1.x cron作业。

   但是，如果在迁移期间需要运行某些作业，请确保它们不会创建新数据库实体，也不会更改现有实体，以免这些实体无法通过Delta模式进行处理。

   例如，`enterprise_salesarchive_archive_orders` cron作业将旧订单移动到存档。 在迁移期间运行此作业是安全的，因为增量模式可识别此作业并正确处理归档的订单。

1. 使用[!DNL Data Migration Tool]迁移设置和网站。

1. 将Magento1.x媒体文件复制到Magento2.x。

   您必须将这些文件从`magento1-root/media`目录手动复制到`magento2-root/pub/media`。

1. 使用[!DNL Data Migration Tool]将数据从Magento1数据库批量复制到Magento2数据库。

   如果某些扩展包含要迁移的数据，则可能需要安装这些适用于Magento2的扩展。 如果Magento2数据库中的扩展名具有不同的结构，请使用随[!DNL Data Migration Tool]提供的映射文件。

1. 重新索引所有Magento2.x索引器。 有关详细信息，请参阅&#x200B;_配置指南_&#x200B;中的[管理索引器](../../configuration/cli/manage-indexers.md)。

## 步骤5：根据需要更改迁移的数据

有时，您可能希望在迁移后让您的Magento2存储具有不同的目录结构、销售规则和CMS页面。

在进行手动数据更改时，务必要谨慎。 错误会在后续的增量数据迁移步骤中创建错误。

例如，从Magento2中删除的产品：已在实时Magento1商店中购买且在您的Magento2商店中不再可用的产品。 在增量模式下运行[!DNL Data Migration Tool]时，传输有关此类购买的数据可能会导致错误。

## 步骤6：更新增量数据

在迁移数据后，您必须增量捕获已添加到Magento1存储区的数据更新（如新订单、审查和客户配置文件中的更改），并使用增量模式将这些更新传输到Magento2存储区。

* 开始增量迁移；更新将持续运行。 您可以随时按`Ctrl+C`来停止传输更新。

* 在此期间，请测试您的Magento2站点，以尽快发现任何问题。 如果遇到问题，请按`Ctrl+C`停止增量迁移，并在解决问题后重新启动。

>[!NOTE]
>
>如果您同时对Magento2站点执行测试并运行迁移过程，则可能会出现卷检查警告。 发生这种情况的原因是，在Magento2中创建了Magento1实例中不存在的实体。

## 步骤7：上线

现在，您的Magento2站点已与Magento1保持同步并且正常运行，请执行以下操作以切换到新站点：

1. 将Magento1系统置于维护模式(DOWNTIME STARTS)。

1. 在迁移工具命令窗口中按Ctrl+C可停止增量更新。

1. 启动Magento2 cron作业。

1. 在Magento2系统中，重新索引股票索引器。 有关详细信息，请参阅[配置指南]。

1. 使用您选择的工具，在客户使用您的店面之前，点击Magento2系统中的页面以缓存页面。

1. 对您的Magento2站点执行任何最终验证。

1. 更改DNS、负载平衡器等以指向新的生产硬件(DOWNTIME ENDS)。

1. Magento2商店现已准备就绪，可供使用。 您和您的客户可以恢复所有活动。

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
