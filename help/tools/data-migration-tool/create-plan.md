---
title: 创建数据迁移计划
description: 请按照以下步骤创建数据迁移计划，以确保成功从Magento1升级到Magento2。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 创建数据迁移计划

要成功迁移并避免出现问题，您需要全面规划并测试迁移。

## 开始之前：考虑升级

迁移是进行重大更改并为网站的下一级增长做好准备的绝佳时机。 考虑是否需要使用更多硬件来设计新站点，还是需要使用更高级的拓扑来设计更好的缓存层。

## 步骤1:查看当前网站上的扩展

* 您安装了哪些扩展？

* 您是否已确定是否需要新网站上的所有这些扩展？ 也许有些旧的可以安全地删除。

* 是否确定扩展的Magento2版本存在？ 访问 [Commerce Marketplace] 要查找最新版本，或联系扩展提供商。

* 要迁移扩展中的哪些数据库资产？

## 步骤2:构建并准备存储以进行迁移

* 使用拓扑和设计来设置Magento2硬件系统，至少与您现有的Magento1系统相匹配

* 安装Magento2.x（包含此版本的所有模块）和 [!DNL Data Migration Tool] 在符合 [Magento系统要求]

* 对 [!DNL Data Migration Tool] 代码，以防您不需要迁移某些数据（如CMS页面、销售规则），或希望在迁移期间转换Magento自定义。 阅读 [!DNL Data Migration Tool]&#39;s [技术规范](technical-specification.md) 更好地了解从内部迁移的方式

## 步骤3:干跑

在生产环境中开始迁移之前，最好先在测试环境中完成所有迁移步骤。

在此类迁移测试中，请执行以下步骤：

* 将您的Magento1存储复制到暂存服务器

* 将复制的Magento1存储完全迁移到Magento2

* 彻底测试新商店

## 步骤4:开始迁移

1. 确保 [!DNL Data Migration Tool] 具有连接到Magento1和Magento2数据库的网络访问权限。 在防火墙中打开相应的端口。

1. 在Magento1.x管理面板中停止所有活动（订单管理除外），例如发运、创建发票和贷项通知单。 通过调整 [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >在Magento2存储上线之前，不得继续这些活动。

1. 我们建议停止所有Magento1.x cron作业。

   但是，如果迁移期间需要运行某些作业，请确保它们不会创建新数据库实体或更改现有数据库实体，因为此类实体无法通过增量模式进行处理。

   例如， `enterprise_salesarchive_archive_orders` cron作业将旧订单移至存档。 迁移期间运行此作业是安全的，因为增量模式可识别此作业并正确处理已存档的订单。

1. 使用 [!DNL Data Migration Tool] 迁移设置和网站。

1. 将Magento1.x媒体文件复制到Magento2.x。

   您必须从 `magento1-root/media` 目录 `magento2-root/pub/media`.

1. 使用 [!DNL Data Migration Tool] 将您的数据从Magento1数据库批量复制到Magento2数据库。

   如果某些扩展包含要迁移的数据，您可能需要安装适用于Magento2的这些扩展。 如果扩展在Magento2数据库中具有不同的结构，请使用随 [!DNL Data Migration Tool].

1. 重新编入所有Magento2.x索引器的索引。 有关详细信息，请参阅 [配置指南].

## 步骤5:对迁移的数据进行更改（如果需要）

有时，迁移后您可能希望Magento2存储具有不同的目录结构、销售规则和CMS页面。

在手动更改数据时务必要谨慎。 错误会在后续的增量数据迁移步骤中导致错误。

例如，从Magento2中删除的产品：已在实时Magento1商店中购买的，且在Magento2商店中不再可用的。 传输有关此类购买的数据可能会在运行 [!DNL Data Migration Tool] 在增量模式下。

## 步骤6:更新增量数据

迁移数据后，您必须以增量方式捕获已添加到Magento1存储中的数据更新（例如新订单、审阅和客户配置文件的更改），并使用增量模式将这些更新传输到Magento2存储。

* 启动增量迁移；更新会持续运行。 您可以随时通过按 `Ctrl+C`.

* 在此期间测试您的Magento2网站，以尽快发现任何问题。 如果遇到问题，请按 `Ctrl+C` 以停止增量迁移，并在您解决问题后重新启动该迁移。

>[!NOTE]
>
>如果您对Magento2站点进行测试并同时运行迁移过程，则可能会出现批量检查警告。 之所以会发生这种情况，是因为在Magento2中，您创建的实体在Magento1实例中不存在。

## 步骤7:上线

现在，您的Magento2网站已与Magento1保持最新且正常运行，请执行以下操作以切换到新网站：

1. 将Magento1系统置于维护模式（停机开始）。

1. 在迁移工具命令窗口中按Control+C以停止增量更新。

1. 启动Magento2 cron作业。

1. 在Magento2系统中，重新编入股票索引器的索引。 有关更多信息，请参阅 [配置指南].

1. 使用您选择的工具，在使用您的店面的客户之前，点击Magento2系统中的页面以缓存页面。

1. 对您的Magento2网站执行任何最终验证。

1. 更改DNS、负载平衡器等以指向新的生产硬件（停机结束）。

1. Magento2商店现已准备就绪。 您和您的客户可以恢复所有活动。

<!-- LINK ADDRESSES -->
[Magento系统要求]: ../../installation/system-requirements.md
[Commerce Marketplace]: https://marketplace.magento.com
[配置指南]: ../../configuration/cli/manage-indexers.md
