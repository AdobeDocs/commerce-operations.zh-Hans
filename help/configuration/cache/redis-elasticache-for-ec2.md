---
title: 使用AWS ElastiCache配置Redis
description: 对于在EC2上托管的Commerce实例，了解如何使用AWS ElastiCache代替本地Redis实例。 了解命令行设置、配置选项和验证技术。
feature: Configuration, Cache
source-git-commit: 908796587e78b80d699354c0506ca948d0f37518
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# 使用AWS ElastiCache配置Redis

从Commerce 2.4.3开始，在Amazon EC2上托管的实例可能使用AWS ElastiCache来代替本地Redis实例。

>[!WARNING]
>
>本节仅适用于在Amazon EC2 VPC上运行的Commerce实例。 它不适用于内部部署。

## 先决条件

- **创建Redis OSS无服务器缓存** — 从AWS管理控制台中，在EC2实例的同一区域和VPC中创建Redis缓存。 有关说明，请参阅[AWS Elasticache文档]&#x200B;(https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html)。

- **验证与您的EC2 Commerce实例的连接**

   - 打开EC2实例的SSH连接
   - 在EC2实例上，安装Redis客户端：

     ```bash
     sudo apt-get install redis
     ```

   - 将入站规则添加到EC2安全组：类型`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 将入站规则添加到ElastiCache群集安全组：类型`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 连接到Redis CLI：

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### 配置Commerce以使用群集

Commerce支持多种类型的缓存配置。 通常，缓存配置在前端和后端之间拆分。 前端缓存被分类为`default`，用于任何缓存类型。 您可以自定义或拆分为较低级别的缓存以实现更好的性能。 一种常见的Redis配置是将默认高速缓存和页面高速缓存分隔到各自的Redis数据库(RDB)中。

运行`setup`命令以指定Redis端点。

要将Commerce for Redis配置为默认缓存：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

要为Redis页面缓存配置Commerce，请执行以下操作：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

要将Commerce配置为使用Redis进行会话存储，请执行以下操作：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## 验证连通性

**要验证Commerce是否正在与ElastiCache通信**：

1. 打开到Commerce EC2实例的SSH连接。
1. 启动Redis显示器。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. 在Commerce UI中打开页面。
1. 验证终端中的[缓存输出](#verify-the-redis-connection)。
