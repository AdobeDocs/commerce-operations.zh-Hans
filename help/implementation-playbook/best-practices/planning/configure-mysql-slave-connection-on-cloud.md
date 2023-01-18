---
title: 配置MySQL从连接的最佳实践
description: 了解如何为部署在云基础架构上的Adobe Commerce站点配置MySQL从连接。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 0866272e02a7a223d35e14842bfb42a827e0468d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# 配置MySQL从连接的最佳实践

>!![NOTE]
我们知道，本文仍包含一些行业标准软件术语，有些术语可能会发现带有种族主义、性别歧视或压迫性，并可能会让读者感到受伤、受到创伤或不受欢迎。 Adobe正在努力从我们的代码、文档和用户体验中删除这些术语。

对于在云基础架构Pro架构上部署的Adobe Commerce站点，Adobe建议默认启用数据库的MYSQL从连接。

Adobe Commerce可以异步读取多个数据库。  启用MYSQL从连接时，Adobe Commerce会使用与数据库的只读连接来接收非主控节点上的只读流量。 这通过负载平衡提高了性能，因为只有一个节点需要处理读写流量。

## 受影响的版本

Adobe Commerce云基础架构、专业架构

## 配置MySQL从连接

MYSQL从连接的配置由 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 在云基础架构环境配置文件的Adobe Commerce中部署变量， `.magento.env.yaml`. 将此变量设置为 `true` 以启用连接。

要启用MySQL从连接，请执行以下操作：

1. 编辑 `.magento.env.yaml` 文件并验证 `MYSQL_USE_SLAVE_CONNECTION` 启用。

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 提交任何更改，然后将其推送到环境分支以部署更新。

   成功完成部署后，将在您的云基础架构上启用MySQL从连接。

## 其他信息

- [环境变量](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [云基础架构上的Adobe Commerce中的MySQL高负载瓶颈](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [云基础架构上的Adobe Commerce数据库最佳实践](database-on-cloud.md)
