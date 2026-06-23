---
title: 使用AWS ElastiCache配置Redis
description: 了解如何将AWS ElastiCache用作EC2上Adobe Commerce的Redis后端。 发现命令行设置、配置和验证。
feature: Configuration, Cache
autotag-review: '2026-06-22T21:54:39.355Z'
TQID: 'https://experienceleague.adobe.com/p4-Pyc3yWwokyFOAyAjN3r1Ic26brx83bPf-GZQNSN8'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: fbb1d92d5f8537e6f1436cd985af120114883df6
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---


# 使用AWS ElastiCache配置Redis

从Commerce 2.4.3开始，在Amazon EC2上托管的实例可能使用AWS ElastiCache来代替本地Redis实例。

>[!WARNING]
>
>本节仅适用于在Amazon EC2 VPC上运行的Commerce实例。

## 先决条件

- **创建Redis OSS无服务器缓存** — 从AWS管理控制台中，在EC2实例的同一区域和VPC中创建Redis缓存。 有关说明，请参阅[AWS Elasticache文档](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html)。

- **验证与您的EC2 Commerce实例的连接**

   - 打开EC2实例的SSH连接
   - 在EC2实例上，安装Redis客户端：

     ```shell
     sudo apt-get install redis
     ```

   - 将入站规则添加到EC2安全组：类型`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 将入站规则添加到ElastiCache群集安全组：类型`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 连接到Redis CLI：

     ```shell
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### 配置Commerce以使用群集

Commerce支持多种类型的缓存配置。 通常，缓存配置在前端和后端之间拆分。 前端缓存被分类为`default`，用于任何缓存类型。 您可以自定义或拆分为较低级别的缓存以实现更好的性能。 一种常见的Redis配置是将默认高速缓存和页面高速缓存分隔到各自的Redis数据库(RDB)中。

运行`setup`命令以指定Redis端点。

要将Commerce for Redis配置为默认缓存：

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

要为Redis页面缓存配置Commerce，请执行以下操作：

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

要将Commerce配置为使用Redis进行会话存储，请执行以下操作：

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## 验证连通性

**要验证Commerce是否正在与ElastiCache通信**：

1. 打开到Commerce EC2实例的SSH连接。
1. 启动Redis显示器。

   ```shell
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. 在Commerce UI中打开页面。
1. 验证终端中的[缓存输出](#verify-connectivity)。
