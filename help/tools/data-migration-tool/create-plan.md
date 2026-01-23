---
title: 创建数据迁移计划
description: 了解如何创建从Magento 1升级到Magento 2的数据迁移计划。 规划和测试您的迁移以避免出现问题。
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# 创建数据迁移计划

要成功迁移并避免出现问题，您需要彻底规划和测试迁移。

## 开始之前：请考虑升级

迁移是进行重大更改并使您的站点为下一级别的增长做好准备的好时机。 考虑您的新站点是需要设计额外的硬件，还是需要设计更高级的拓扑结构，以便提供更好的缓存层。

## 步骤1：查看当前网站上的扩展

* 您安装了哪些扩展？

* 您是否确定新网站上是否需要所有这些扩展？ 可能有可以安全移除的旧项目。

* 是否确定存在Magento 2版本的扩展？ 请访问[Commerce Marketplace](https://commercemarketplace.adobe.com/)以查找最新版本，或与扩展提供商联系。

* 您要迁移扩展中的哪些数据库资产？

## 步骤2：构建并准备存储以进行迁移

* 使用至少与现有Magento 1系统匹配的拓扑和设计来设置Magento 2硬件系统

* 在符合[!DNL Data Migration Tool]系统要求[的系统上安装Magento 2（包含此版本的所有模块）和](../../installation/system-requirements.md)

* 自定义[!DNL Data Migration Tool]代码以跳过某些数据(如CMS页面、销售规则)，或在迁移期间转换自定义设置。 阅读[!DNL Data Migration Tool]的[技术规范](technical-specification.md)以了解有关迁移工作方式的更多信息

## 步骤3：练习

在生产环境中开始迁移之前，请先在测试环境中完成所有迁移步骤。

在此类迁移测试中，请执行以下步骤：

* 将Magento 1商店复制到暂存服务器

* 将复制的Magento 1存储完全迁移到Magento 2

* 彻底测试您的新商店

## 步骤4：开始迁移

1. 确保[!DNL Data Migration Tool]具有连接到Magento 1和Magento 2数据库的网络访问权限。 在防火墙中打开相应的端口。

1. 停止Magento 1管理面板中的所有活动(Order Management除外)，例如送货、创建发票和贷项通知单。 可以通过调整[!DNL Data Migration Tool]中Delta模式的设置来扩展允许的活动列表。

   >[!NOTE]
   >
   >在Magento 2应用商店上线之前，请勿恢复这些活动。

1. 我们建议停止所有Magento 1 cron作业。

   如果某些作业必须在迁移期间运行，请确保它们不会以增量模式无法处理的方式创建或修改数据库实体。

   例如，`enterprise_salesarchive_archive_orders` cron作业将旧订单移动到存档。 在迁移期间运行此作业是安全的，因为增量模式可识别此作业并正确处理归档的订单。

1. 使用[!DNL Data Migration Tool]迁移设置和网站。

1. 将Magento 1媒体文件复制到Magento 2。

   将这些文件从`magento1-root/media`目录手动复制到`magento2-root/pub/media`。

1. 使用[!DNL Data Migration Tool]将数据从Magento 1数据库批量复制到Magento 2数据库。

   如果您的某些扩展包含要迁移的数据，则可能需要安装这些适用于Magento 2的扩展。 如果扩展名在Magento 2数据库中具有不同的结构，请使用随[!DNL Data Migration Tool]提供的映射文件。

1. 重新索引所有Magento 2索引器。 有关详细信息，请参阅[配置指南](../../configuration/cli/manage-indexers.md)中的&#x200B;_管理索引器_。

## 步骤5：根据需要更改迁移的数据

有时，您可能希望在迁移后让Magento 2商店具有不同的目录结构、销售规则和CMS页面。

在进行手动数据更改时，务必要谨慎。 错误会在后续的增量数据迁移步骤中创建错误。

例如，从Magento 2中删除的产品：已在您的Magento 1实时商店中购买且在您的Magento 2商店中不再可用的产品。 在增量模式下运行[!DNL Data Migration Tool]时，传输有关此类购买的数据可能会导致错误。

## 步骤6：更新增量数据

在迁移数据之后，使用增量模式捕获增量更新，并将其从Magento 1传输到Magento 2（例如新订单、审查和客户配置文件更改）。

* 开始增量迁移；更新将持续运行。 您可以随时按`Ctrl+C`来停止传输更新。

* 在此期间，请测试您的Magento 2网站，以尽快发现任何问题。 如果遇到问题，请按`Ctrl+C`停止增量迁移，并在解决问题后重新启动。

>[!NOTE]
>
>如果您同时对Magento 2站点执行测试并运行迁移过程，则可能会显示卷检查警告。 发生这种情况的原因是，在Magento 2中，您创建的实体在Magento 1实例中不存在。

## 步骤7：上线

完全迁移Magento 2站点并正常运行后，请完成以下转换：

1. 将Magento 1系统置于维护模式（停机时间开始）。

1. 在迁移工具命令窗口中按Ctrl+C可停止增量更新。

1. 启动Magento 2 cron作业。

1. 在您的Magento 2系统中，重新索引股票索引器。 有关详细信息，请参阅[配置指南](../../configuration/cli/manage-indexers.md)中的&#x200B;_管理索引器_。

1. 使用您选择的工具，在Magento 2系统中点击页面，以便在客户使用您的店面之前缓存页面。

1. 对您的Magento 2站点执行任何最终验证。

1. 更改DNS、负载平衡器等以指向新的生产硬件(DOWNTIME ENDS)。

1. Magento 2商店现已准备就绪，可供使用。 您和您的客户可以恢复所有活动。
