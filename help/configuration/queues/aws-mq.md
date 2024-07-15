---
title: 设置Amazon消息队列
description: 了解如何配置Commerce以使用AWS MQ服务。
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 设置Amazon消息队列

自Commerce 2.4.3起，Amazon Message Queue (MQ)可用作本地消息队列实例的云就绪替代项。

要在AWS上创建消息队列，请参阅&#x200B;_Amazon文档_&#x200B;中的[设置AWS MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html)。

## 为AWS MQ配置Commerce

要连接到AWS MQ服务，请在`env.php`文件中配置`queue.amqp`对象。
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

- `host` - AMQP端点的URL；可通过在AWS中单击Broker名称使用(删除“https://”和尾随端口号)
- `user` — 创建AWS MQ代理时输入的用户名值
- `password` — 创建AWS MQ代理时输入的密码值

>[!INFO]
>
>Amazon MQ仅支持TLS连接。 不支持对等验证。

编辑`env.php`文件后，请运行以下命令以完成安装：

```bash
bin/magento setup:upgrade
```

## Commerce如何使用AWS MQ服务

`async.operations.all`消息队列使用者使用AMQP连接。

此使用者通过AWS MQ连接路由任何前缀为`async`的主题名称。

例如，在`InventoryCatalog`中有：

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

`InventoryCatalog`的默认配置不会将消息发布到[!DNL RabbitMQ]；默认行为是在同一用户线程中执行该操作。 要告知`InventoryCatalog`发布消息，请启用`cataloginventory/bulk_operations/async`。 从管理员转到&#x200B;**商店** >配置> **目录** > **库存** >管理员批量操作，并将`Run asynchronously`设置为&#x200B;**是**。

## 测试消息队列

要测试从Commerce向[!DNL RabbitMQ]发送的消息，请执行以下操作：

1. 登录到AWS中的[!DNL RabbitMQ] Web控制台以监视队列。
1. 在“管理员”中，创建产品。
1. 创建库存来源。
1. 启用&#x200B;**存储** >配置> **目录** > **库存** >管理员批量操作>异步运行。
1. 转到&#x200B;**目录** >产品。 从网格中，选择上面创建的产品，然后单击&#x200B;**分配库存Source**。
1. 单击&#x200B;**保存并关闭**&#x200B;以完成该过程。

   您现在应会在[!DNL RabbitMQ] Web控制台中看到消息。

1. 启动`async.operations.all`消息队列使用者。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

现在，您应会在[!DNL RabbitMQ] Web控制台中看到已处理排队消息。
在“管理员”中验证产品上的库存来源是否已更改。
