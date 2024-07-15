---
title: 拆分数据库性能解决方案
description: 阅读有关Adobe Commerce的拆分数据库解决方案的信息。
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 拆分数据库解决方案概述

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce具有多种可扩展性优势，包括能够为Commerce应用程序的不同功能区域使用三个单独的master数据库。

结帐、订单和产品数据都可以使用单独的master数据库，您可以选择复制该数据库。 此分离可根据您的需求，独立缩放网站结账、订单管理活动、网站浏览和促销活动的负载。 这些更改在如何扩展数据库层方面提供了相当大的灵活性。

>[!INFO]
>
>云基础架构上的Adobe Commerce _不_&#x200B;支持此功能。

`ResourceConnections`类提供到Commerce应用程序的统一MySQL数据库连接。 对于主数据库的查询，我们实现了命令查询职责划分(CQRS)数据库模式。 此模式处理将读取和写入查询路由到相应数据库的逻辑。 开发人员不需要知道正在使用哪种配置，并且没有单独的读取和写入数据库连接。

如果设置可选的数据库复制，则具有以下优势：

- 数据备份
- 在不影响master数据库的情况下进行数据分析
- 可扩展性

MySQL数据库以异步方式复制，这意味着无需永久连接从属进程即可从主数据库接收更新。

下图显示了此功能的工作方式。

![Adobe Commerce使用其他数据库存储表](../../assets/configuration/split-db-diagram-ee.png)

在Magento Open Source中，只使用一个master数据库。

Adobe Commerce使用三个主数据库和可配置数量的从属数据库进行复制。 Adobe Commerce具有用于数据库连接的单一接口，可实现更快的性能和更好的可扩展性。

## 配置选项

由于拆分数据库性能解决方案的设计方式，您的自定义代码和已安装的组件&#x200B;_无法_&#x200B;执行以下任何操作：

- 直接写入数据库(相反，您必须使用Adobe Commerce数据库界面)
- 使用影响销售或报价数据库的JOIN
- 对结帐、销售或主数据库中的表使用外键

>[!WARNING]
>
>联系组件开发人员以验证其组件是否执行了上述任何操作。 如果是这样，您必须仅选择下列选项之一：
>
>- 要求组件开发人员更新其组件。
>- 按原样&#x200B;_使用组件，但不使用_&#x200B;拆分数据库解决方案。
>- 删除组件，以便使用拆分数据库解决方案。

这也意味着您可以：

- 在将拆分数据库解决方案&#x200B;_投入生产之前_&#x200B;配置Commerce。

  Adobe建议在安装Commerce软件后尽快配置拆分数据库。

- [手动配置](multi-master-manual.md)拆分数据库解决方案。

  如果您已安装组件或Commerce已在生产环境中，则必须执行此任务。 （_不_&#x200B;更新生产系统；在开发系统中进行更新，并在测试更改后同步这些更改。）

  >[!WARNING]
  >
  >必须手动备份另外两个数据库实例。 Commerce仅备份主数据库实例。 [`magento setup:backup --db`](../../installation/tutorials/backup.md)命令和Admin选项不备份其他表。

## 先决条件

拆分数据库要求您在任意主机上设置三个MySQL master数据库(所有三个数据库都在Commerce服务器上，每个数据库在单独的服务器上，等等)。 这些是&#x200B;_master_&#x200B;数据库，其使用方式如下：

- 一个签出表的主数据库
- 一个Master数据库，用于Sales表(也称为&#x200B;_Order Management System_&#x200B;或&#x200B;_OMS_，表)
- 一个master数据库，用于Commerce 2应用程序表的其余部分

此外，您还可以选择设置任意数量的&#x200B;_从属_&#x200B;数据库，用作负载平衡器和备份。

本指南讨论如何仅设置master数据库。 我们提供示例配置和参考，供您根据需要设置从属数据库。

在本指南中，将命名三个主数据库：

- `magento_quote`
- `magento_sales`
- `magento`

（您可以随意命名数据库。）
