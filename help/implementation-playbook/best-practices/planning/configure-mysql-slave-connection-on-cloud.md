---
title: 配置MySQL从连接的最佳实践
description: 了解如何为部署在云基础架构上的Adobe Commerce站点配置MySQL从连接。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 配置MySQL从连接的最佳实践

>[!NOTE]
>
>本文包含一些行业标准软件术语，有些术语可能会发现带有种族主义、性别歧视或压迫性，并且可能会让读者感到受伤、受到创伤或不受欢迎。 Adobe正在努力从我们的代码、文档和用户体验中删除这些术语。

对于在云基础架构Pro架构上部署的Adobe Commerce站点，Adobe建议默认启用数据库的MYSQL从连接。

Adobe Commerce可以异步读取多个数据库。 启用MYSQL从连接时，Adobe Commerce会使用与数据库的只读连接来接收非主控节点上的只读流量。 当只有一个节点处理读写流量时，通过负载平衡来提高性能。

## 受影响的版本

Adobe Commerce云基础架构、专业架构

## 配置MySQL从连接

在云基础架构上的Adobe Commerce中，您可以通过设置 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 变量。 将此变量设置为true可自动使用与数据库的只读连接。

**启用MySQL从连接**:

1. 在本地工作站上，请更改到项目目录。

1. 在 `.magento.env.yaml` 文件，设置 `MYSQL_USE_SLAVE_CONNECTION` 为真。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 提交 `.magento.env.yaml` 文件更改并推送到远程环境。

   成功完成部署后，将为云环境启用MySQL从连接。

了解有关通过使用覆盖现有商务配置来自定义云环境的更多信息 [环境变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 在 _Adobe Commerce云基础架构指南_.

## 其他信息

- [云基础架构上的Adobe Commerce中的MySQL高负载瓶颈](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [云基础架构上的Adobe Commerce数据库最佳实践](database-on-cloud.md)
