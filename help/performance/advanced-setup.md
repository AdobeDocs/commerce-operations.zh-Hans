---
title: 高级设置
description: 针对旨在处理大量数据的大型企业系统审查最佳实践和建议。
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# 高级设置

[!DNL Commerce] 是一款高度灵活且可伸缩的产品，包含适用于各种规模商家的解决方案。 此部分介绍了有关配置的最佳实践和建议 [!DNL Commerce] 用于处理大量数据、极端负载和其他企业案例。

## 校准索引性能

在处理大量数据时，重新索引可能会成为一个问题。 此 [!DNL Commerce] 团队选择了加载量最大的索引并启用了批量索引，这允许您设置要在每个迭代上处理的数据的一部分。 这样，用户就可以根据数据库中数据的类型和大小调整批量大小。

要管理此设置，请编辑 `batchRowsCount` 中的参数 `di.xml` 相应模块的文件。 以下索引支持此功能：

* 类别产品索引（目录模块）
* 价格指数（目录模块）
* EAV索引（目录模块）
* 股票指数（CatalogInventory模块）

您可以通过调整索引批量处理大小变量来调整索引器性能。 这控制索引器一次处理的实体数。 在某些情况下，我们发现索引时间显着减少。

例如，如果运行类似B2B Medium的配置文件，则可以覆盖配置值 `batchRowsCount` 在 `app/code/Magento/catalog/etc/di.xml` 并覆盖默认值 `5000` 到 `1000`. 默认情况下，这会将完整索引时间从4小时缩短到2小时 [!DNL MySQL] 配置。

>[!NOTE]
>
>我们尚未为目录规则索引器启用批量处理。 拥有大量目录规则的商家需要调整其目录规则 [!DNL MySQL] 优化索引时间的配置。 在本例中，编辑 [!DNL MySQL] 配置文件并为TMP_TABLE_SIZE和MAX_HEAP_TABLE_SIZE配置值分配更多内存（两者缺省为16M）将提高此索引器的性能，但将导致 [!DNL MySQL] 占用更多RAM。

### 按网站限制客户组和共享目录

大量产品SKU、网站、客户组或共享目录将影响产品价格和目录规则索引器的运行时间。 这是因为默认情况下，所有网站都会分配给所有客户组（共享目录）。

要缩短索引时间，您可以 [从客户组排除某些网站（共享目录）](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## 设置Redis

有时，一个Redis实例不足以处理传入的请求。 要解决这种情况，我们可以建议采用几种解决方案。

首先， [!DNL Commerce] 允许您为每种缓存类型配置单独的缓存存储。 这样，您可以安装与在Magento中注册的缓存类型数相同数量的单独Redis实例。 实际上，您可能希望最常用缓存的Redis实例，例如配置、布局和块。

另一种解决方案是将配置缓存放在文件系统上，并将其他缓存移动到Redis服务器。 使用此解决方案，您需要一个单独的工具来集中使所有Web节点上的配置缓存失效。

您还可以使用一个Redis群集，该群集执行自动增加节点数的并行读/写操作。 [!DNL Commerce] 不提供此情况的配置，但可以通过少量自定义来启动它。

## 设置 [!DNL RabbitMQ]

Adobe Commerce支持通过实现的消息队列 [!DNL RabbitMQ]. [!DNL Commerce] 使用此服务执行大量异步操作，包括B2B目录操作和异步库存更新。 所有用于将更多作业添加到作业服务器的界面都随产品一起分发，并可用于第三方扩展范围内的自定义异步逻辑实施。 与任何其他集成一样， [!DNL Commerce] 提供了样例配置文件，用于 [!DNL RabbitMQ] 该库包含所有推荐的设置并已完全准备好用于生产。

## 拆分数据库

>[!WARNING]
>
>拆分数据库功能是 [已弃用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 在Adobe Commerce版本2.4.2中。 请参阅 [从拆分数据库还原到单个数据库](../configuration/storage/revert-split-database.md).

Adobe Commerce允许您配置可扩展的数据库存储，以满足不断增长的业务的需要。 您可以设置三个独立的主数据库，为特定域提供服务：

* 主（目录）数据库
* 签出数据库
* 订单管理系统(OMS)数据库

要配置其他数据库，必须创建一个空数据库并运行以下命令之一：

用于签出主数据库

```bash
bin/magento setup:db-schema:split-quote
```

对于OMS主数据库

```bash
bin/magento setup:db-schema:split-sales
```

这些命令将特定域表从主数据库迁移到域数据库。 它们还会更改 [!DNL Commerce] 配置以允许相应的连接和约束处理。

通过为结账和订单管理设置单独的数据库，您可以在数据库服务器之间分配负载。 您可以每秒提供更多的结账并处理更多订单，而不会影响目录和其他操作的可用性。 我们建议在瞬间或活跃销售期间拆分数据库，或永久用于自然高负载项目。 应在系统管理员的监督下执行当前数据在数据库之间的迁移。  在生产模式下请勿拆分数据库。

除了master数据库， [!DNL Commerce] 用于配置多个从属数据库（系统中声明的每个数据资源各一个）。 从属数据库用作主数据库或域主数据库之一的完整复制副本。 它针对特定资源的读取操作发出。

您可以通过运行以下命令来添加从属数据库：

```bash
bin/magento setup:db-schema:add-slave
```

此命令执行配置更改，但不配置复制本身。 这应该手动完成。

拆分主数据库并设置从属数据库后， [!DNL Commerce] 自动调节与特定数据库的连接，根据请求类型(POST、PUT、GET等)和数据资源做出决策。 如果 [!DNL Commerce] 或者，扩展对GET请求执行写操作，系统自动将连接从从数据库切换到主数据库。 它与master数据库的工作方式相同：一旦您使用与签出相关的表，系统就会将所有查询重定向到特定数据库。 同时，所有与目录相关的查询将转到主数据库。

有关配置和多个主/从配置优点的更多详细信息，请参见
[拆分数据库性能解决方案](../configuration/storage/multi-master.md).

## 提供媒体内容

Magento不提供任何特定的集成来服务和交付媒体内容。 可在Magento中一起使用所有常用方法。

提供媒体内容的最简单方法是在页面上交付和缓存媒体内容， [!DNL Varnish] 服务器。 此方法假定使用共享文件系统来存储媒体内容，或者使用专用服务器指向 [!DNL Varnish].

对于中负载和高负载环境，我们建议使用内容交付网络(CDN)服务，如Fastly、Akamai和其他服务。 在使用这些服务时， [!DNL Commerce] 使用经典的“拉”方法进行内容更新。 您必须配置 [!DNL Commerce] 用于相应CDN服务的URL。 通过将媒体内容移动到CDN，可以显着减少实例的负载。

## 配置日志存储

日志的存储及其对其他磁盘操作的影响会影响Web节点的可用性，特别是在高负载情况下。 如果您不需要日志记录，我们建议您将其最小化。 您还可以配置日志记录，使其在独立的高访问速度存储系统上写入。 请注意，访问日志存储的任何瓶颈都可能会直接影响作为流的一部分记录写入或读取操作的传入请求的处理。
