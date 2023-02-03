---
title: 数据迁移的工作原理
description: 了解Magento1和Magento2之间的数据迁移过程，包括术语、工作流图和步骤。
source-git-commit: be2f924728853236bba786e7611b2a368c9f3054
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---


# 数据迁移的工作原理

本主题简要概述如何使用将Magento1迁移到Magento2 [!DNL Data Migration Tool].

的 [!DNL Data Migration Tool] 是用于将数据从Magento1传输到Magento2的命令行界面(CLI)工具。 该工具可验证Magento1和2数据库结构（表和字段）之间的一致性，跟踪数据传输进度，创建日志，并运行数据验证测试。

## 术语

* **模式**  — 一组有序的操作，用于将Magento1.x迁移到Magento2.x。
* **步骤**  — 以定义要迁移的数据类型的模式执行的任务。
* **阶段**  — 验证、传输和验证数据的步骤中的任务。
* **映射文件**  — 定义Magento1.x和Magento2.x数据结构之间的规则和连接以完成阶段的XML文件。

## 模式

的 [!DNL Data Migration Tool] 将迁移过程分为三个阶段或 *模式* 以便将数据从Magento1.x传输和调整到Magento2.x。此处列出了三种模式，必须按此顺序运行：

1. **设置模式**:迁移系统配置和与网站相关的设置。
1. **数据模式**:批量迁移数据库资产。
1. **增量模式**:迁移增量更改（自上次运行以来所做的更改），如新客户和订单。

![迁移模式](../../assets/data-migration/MigrationModes2.png)

## 步骤

的 [!DNL Data Migration Tool] 使用 *步骤* 来迁移特定类型的数据。 例如，在设置模式下，可使用两个步骤迁移所有设置数据：存储步骤和设置步骤。 有关在这些步骤中迁移的特定数据（以及其他模式中的步骤）的详细信息，请参阅 [[!DNL Data Migration Tool] 技术规范](technical-specification.md).

![迁移概述](../../assets/data-migration/MigrationOverview2.png)

## 阶段

每个步骤中有三个 *阶段* 以确保正确迁移数据，将始终执行以下命令：

1. **完整性检查**:比较表字段名称、类型和其他信息，以验证Magento1和2数据结构之间的兼容性。
1. **数据传输**:按表从Magento1和2传输数据表。
1. **卷检查**:比较表之间的记录数以验证传输是否成功。

![迁移阶段](../../assets/data-migration/MigrationSteps2.png)

## 映射文件

在迁移流程的最低级别是XML *映射文件*. 的 [!DNL Data Migration Tool] 在步骤的各个阶段中使用映射文件来在Magento1.x和2.x表之间转换不同的数据结构。

例如，当您将Magento Open Source从1.8.0.0数据库转换到Magento Open Source2.x.x时，映射文件会考虑表被重命名的事实，并在目标数据库中相应地重命名该表。 如果数据结构或数据格式没有差异，则 [!DNL Data Migration Tool] 按原样将其（包括由扩展创建的表中的数据）传输到Magento2数据库。

当差异未在映射文件中声明时， [!DNL Data Migration Tool] 显示错误且未启动。

有关映射文件的详细讨论，请参见[!DNL Data Migration Tool] 技术规范]。

## 迁移流程图

![迁移流程](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] 技术规范](technical-specification.md)

我们很高兴您考虑从世界#1商平台(Magento1.x)转移到未来平台(Magento2)。 我们很高兴能够分享有关此过程的详细信息，我们称之为迁移。

## 迁移组件

Magento2迁移包括四个组件：数据、扩展和自定义代码、主题和自定义。

### 数据

我们开发了 **Magento2[!DNL Data Migration Tool]** 以帮助您将所有产品、客户和订单数据、存储配置、促销等高效移动到Magento2。 本指南提供了有关使用该工具迁移数据的工具及最佳实践的信息。

### 扩展和自定义代码

我们一直在与开发社区合作，以帮助您在Magento2中使用Magento1扩展。 现在，我们为向大家介绍 [Commerce Marketplace](https://marketplace.magento.com/)，您可以从中下载或购买最新版本的喜爱扩展。

有关开发适用于Magento2的扩展的更多信息，请参阅 [PHP开发人员指南](https://developer.adobe.com/commerce/php/development/).

### 主题和自定义

Magento2使用新的方法和技术，让商家拥有无与伦比的能力，创造创新的购物体验，并扩展到新的水平。 要利用这些进步，开发人员必须更改其主题和自定义设置。 文档可在线创建Magento2 [主题](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [布局](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)和 [自定义](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## 迁移工作

就像在1.x版本之间（例如从v1.12到v1.14）进行升级一样，从Magento1迁移到Magento2的工作量取决于您构建网站的方式及其自定义程度。
然而，我们不断改进 [!DNL Data Migration Tool] (请参阅 [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) 更多详情);因此，移民工作在不断减少。
