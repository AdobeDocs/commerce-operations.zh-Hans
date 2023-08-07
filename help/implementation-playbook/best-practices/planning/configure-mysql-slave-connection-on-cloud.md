---
title: 配置MySQL从属连接的最佳实践
description: 了解如何为部署在云基础架构上的Adobe Commerce站点配置MySQL从属连接。
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 3532480e2172c39ceb4ec55c9819d5271fd1fcdb
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 配置MySQL从属连接的最佳实践

>[!NOTE]
>
>本文包含行业标准软件术语，有些人可能会认为这些术语具有种族主义、性别歧视或压迫性，并且可能会使读者感到伤害、创伤或不受欢迎。 Adobe正在努力从代码、文档和用户体验中删除这些术语。

Adobe Commerce可以异步读取多个数据库。 如果您预计部署在云基础架构Pro体系结构上的Commerce站点的MySQL数据库负载会很高，则Adobe建议启用MYSQL从连接。

启用MYSQL从属连接时，Adobe Commerce使用到数据库的只读连接来接收非主控节点上的只读通信。 当只有一个节点处理读写通信时，通过负载平衡提高了性能。

## 受影响的版本

云基础架构上的Adobe Commerce，仅限Pro架构

## 配置MySQL从属连接

在云基础架构上的Adobe Commerce中，您可以通过设置 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 变量。 将此变量设置为 `true` 以自动使用到数据库的只读连接。

**启用MySQL从属连接**：

1. 在本地工作站上，转到您的项目目录。

1. 在 `.magento.env.yaml` 文件，设置 `MYSQL_USE_SLAVE_CONNECTION` 为真。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 提交 `.magento.env.yaml` 文件更改并推送到远程环境。

   成功完成部署后，将为云环境启用MySQL从属连接。

## 其他信息

了解有关通过覆盖现有Commerce配置来自定义云环境的更多信息 [环境变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 在 _云基础架构上的Adobe Commerce指南_.

请参阅 [云基础架构上Adobe Commerce中的MySQL高负载瓶颈](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html) 中的文章 _支持知识库_.
