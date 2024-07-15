---
title: 数据迁移的工作方式
description: 了解Magento1和Magento2之间的数据迁移过程，包括术语、工作流程图和步骤。
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# 数据迁移的工作方式

本主题概要介绍如何使用[!DNL Data Migration Tool]将数据从Magento1迁移到Magento2。

[!DNL Data Migration Tool]是一个命令行界面(CLI)工具，用于将数据从Magento1传输到Magento2。 该工具验证Magento1和2数据库结构（表和字段）之间的一致性，跟踪数据传输进度，创建日志，并运行数据验证测试。

## 术语

* **模式** — 用于将数据从Magento1.x迁移到Magento2.x的一组有序操作。
* **步骤** — 模式中的任务，用于定义要迁移的数据类型。
* **暂存** — 步骤中用于验证、传输和验证数据的任务。
* **映射文件** — 用于定义Magento1.x和Magento2.x数据结构之间的规则和连接以完成阶段的XML文件。

## 模式

[!DNL Data Migration Tool]将迁移过程拆分为三个阶段或&#x200B;*模式*，以便将数据从Magento1.x传输并调整到Magento2.x。此处列出了三种模式，必须按此顺序运行：

1. **设置模式**：迁移系统配置和网站相关的设置。
1. **数据模式**：批量迁移数据库资产。
1. **增量模式**：迁移增量更改（自上次运行以来的更改），如新客户和订单。

![迁移模式](../../assets/data-migration/MigrationModes2.png)

## 步骤

[!DNL Data Migration Tool]在每个模式中使用包含&#x200B;*个步骤*&#x200B;的列表来迁移特定类型的数据。 例如，在“设置”模式下，有两个步骤可用于迁移所有设置数据：“存储”步骤和“设置”步骤。 有关每个步骤中迁移的特定数据（以及其他模式中的步骤）的详细信息，可在[[!DNL Data Migration Tool] 技术规范](technical-specification.md)中找到。

![迁移概述](../../assets/data-migration/MigrationOverview2.png)

## 暂存

每个步骤中始终执行三个&#x200B;*阶段*，以确保正确迁移数据：

1. **完整性检查**：比较表字段名称、类型和其他信息，以验证Magento1和2数据结构之间的兼容性。
1. **数据传输**：从Magento1和2中按表传输数据表。
1. **卷检查**：比较表之间的记录数，以验证传输是否成功。

![迁移阶段](../../assets/data-migration/MigrationSteps2.png)

## 映射文件

迁移过程的最低级别是XML *映射文件*。 [!DNL Data Migration Tool]使用步骤阶段中的映射文件在Magento1.x表和2.x表之间转换不同的数据结构。

例如，当您将数据从Magento Open Source1.8.0.0数据库转换到Magento Open Source2.x.x时，映射文件会考虑表被重命名这一事实，并在目标数据库中相应地重命名表。 如果数据结构或数据格式没有差异，[!DNL Data Migration Tool]会按原样将其传输到Magento2数据库，包括来自扩展创建的表的数据。

如果未在映射文件中声明差异，则[!DNL Data Migration Tool]显示错误且不会启动。

映射文件在[[!DNL Data Migration Tool]技术规范]中有更详细的讨论。

## 迁移流程图

![迁移流程](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool]技术规范](technical-specification.md)

我们很高兴您考虑从世界上#1商业平台(Magento1.x)迁移到未来平台(Magento2)。 我们非常高兴与大家分享有关该过程（我们称之为迁移）的详细信息。

## 迁移组件

Magento2迁移包含四个组件：数据、扩展和自定义代码、主题和自定义。

### 数据

我们开发了&#x200B;**Magento2[!DNL Data Migration Tool]**，以帮助您将所有产品、客户和订单数据、商店配置、促销活动等有效地移至Magento2。 本指南提供有关使用该工具迁移数据的信息和最佳实践。

### 扩展和自定义代码

我们一直在与开发社区合作，帮助您在Magento2中使用Magento1扩展。 现在，我们很荣幸地介绍[Commerce Marketplace](https://marketplace.magento.com/)，您可以在其中下载或购买您最喜爱的扩展的最新版本。

有关为Magento2开发扩展的详细信息，请参阅[PHP开发人员指南](https://developer.adobe.com/commerce/php/development/)。

### 主题和自定义

Magento2采用新的方法和技术，使商家拥有无与伦比的能力，可创造创新的购物体验并提升自己的水平。 为了充分利用这些优势，开发人员必须对其主题和自定义进行更改。 联机提供了用于创建Magento2 [主题](https://developer.adobe.com/commerce/frontend-core/guide/themes/)、[布局](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)和[自定义项](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/)的文档。

## 迁移工作

与1.x版本（例如，从v1.12到v1.14）之间的升级一样，从Magento1迁移到Magento2的工作量级别取决于您构建网站的方式及其自定义级别。
但是，我们正在不断改进[!DNL Data Migration Tool]（有关更多详细信息，请参阅[更改日志](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md)）；因此，迁移工作将不断减少。
