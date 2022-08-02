---
title: 设置Amazon消息队列
description: 了解如何配置Commerce以使用AWS MQ服务。
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# 设置Amazon消息队列

自Commerce 2.4.3起，Amazon消息队列(MQ)可用作本地消息队列实例的云就绪替换。

要在AWS上创建消息队列，请参阅 [设置Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 在 _AWS文档_.

## 为AWS MQ配置Commerce

要连接到AWS MQ服务，请配置 `queue.amqp` 对象 `env.php` 文件。
AWS消息队列需要SSL/TLS连接。

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

其中：

- `host`— AMQP端点的url;单击AWS中的代理名称(删除“https://”和尾随端口号)
- `user` — 创建AWS MQ代理时输入的用户名值
- `password` — 创建AWS MQ代理时输入的密码值

>[!INFO]
>
>Amazon MQ仅支持TLS连接。 不支持对等验证。

编辑 `env.php` 文件中，运行以下命令以完成设置：

```bash
bin/magento setup:upgrade
```

## 商务如何使用AWS MQ服务

的 `async.operations.all` 消息队列使用者使用AMQP连接。

此使用者将路由任何前缀为的主题名称 `async` 通过AWS MQ连接。

例如， `InventoryCatalog` 有：

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

的默认配置 `InventoryCatalog` 不向RabbitMQ发布消息；默认行为是在同一用户线程中执行该操作。 告诉 `InventoryCatalog` 要发布消息，请启用 `cataloginventory/bulk_operations/async`. 从管理员，转到 **商店** >配置> **目录** > **库存** >管理员批量操作和设置  `Run asynchronously`to **是**.

## 测试消息队列

要测试从Commerce向RabbitMQ发送的消息，请执行以下操作：

1. 登录到AWS中的RabbitMQ Web控制台，以监视队列。
1. 在管理员中，创建产品。
1. 创建库存来源。
1. 启用 **商店** >配置> **目录** > **库存** >管理员批量操作>异步运行。
1. 转到 **目录** >产品。 从网格中，选择上面创建的产品，然后单击 **分配库存来源**.
1. 单击 **保存并关闭** 以完成该过程。

   现在，您应会看到消息显示在RabbitMQ Web控制台中。

1. 启动 `async.operations.all` 消息队列使用者。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

此时，您应会看到已排队的消息在RabbitMQ Web控制台中得到处理。
在“管理员”中验证产品上的库存源是否已更改。
