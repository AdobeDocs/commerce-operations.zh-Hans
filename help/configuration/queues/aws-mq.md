---
title: 设置Amazon消息队列
description: 了解如何配置Commerce以使用AWS MQ服务。
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 设置Amazon消息队列

自Commerce 2.4.3起，Amazon Message Queue (MQ)可用作本地消息队列实例的云就绪替代项。

要在AWS中创建消息队列，请参阅 [设置Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 在 _AWS文档_.

## 为AWS MQ配置Commerce

要连接到AWS MQ服务，请配置 `queue.amqp` 中的对象 `env.php` 文件。
AWS Message Queue需要SSL/TLS连接。

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

- `host`—AMQP端点的URL；可通过在AWS中单击Broker名称来访问(删除“https://”和尾随端口号)
- `user` — 创建AWS MQ代理时输入的用户名值
- `password` — 创建AWS MQ Broker时输入的密码值

>[!INFO]
>
>Amazon MQ仅支持TLS连接。 不支持对等验证。

编辑之后 `env.php` 文件，运行以下命令以完成安装：

```bash
bin/magento setup:upgrade
```

## Commerce如何使用AWS MQ服务

此 `async.operations.all` 消息队列使用者使用AMQP连接。

此使用者路由带有前缀的任何主题名称 `async` 通过AWS MQ连接。

例如，在 `InventoryCatalog` 有：

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

的默认配置 `InventoryCatalog` 不会将消息发布到 [!DNL RabbitMQ]；默认行为是在同一用户线程中执行该操作。 告诉 `InventoryCatalog` 要发布消息，请启用 `cataloginventory/bulk_operations/async`. 从管理员，转到 **商店** >配置> **目录** > **库存** >管理员批量操作和设置  `Run asynchronously`到 **是**.

## 测试消息队列

测试从Commerce发送到以下对象的消息： [!DNL RabbitMQ]：

1. 登录到 [!DNL RabbitMQ] AWS中的Web控制台用于监视队列。
1. 在“管理员”中，创建产品。
1. 创建库存来源。
1. 启用 **商店** >配置> **目录** > **库存** >管理员批量操作>异步运行。
1. 转到 **目录** >产品。 从网格中，选择上面创建的产品，然后单击 **分配库存来源**.
1. 单击 **保存并关闭** 以完成该过程。

   现在，您应会看到消息出现在 [!DNL RabbitMQ] Web控制台。

1. 启动 `async.operations.all` 消息队列使用者。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

现在，您应会在中看到已处理排队消息 [!DNL RabbitMQ] Web控制台。
在“管理员”中验证产品上的库存来源是否已更改。
