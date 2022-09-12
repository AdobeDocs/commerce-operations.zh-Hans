---
title: 消息代理
description: 请按照以下步骤来安装和配置所需的报文代理软件（如RabbitMQ），以便在本地安装Adobe Commerce和Magento Open Source。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# 消息代理

Adobe Commerce使用RabbitMQ开源消息代理。 它提供可靠、高可用、可扩展和可移植的报文传送系统。

消息队列提供了一种异步通信机制，其中消息的发送者和接收者不会相互联系。 他们也不需要同时与消息队列通信。 当发件人将消息放入队列时，会一直存储到收件人收到消息为止。

在安装Adobe Commerce或Magento Open Source之前，必须建立消息队列系统。 基本顺序是：

1. 安装RabbitMQ和任何先决条件。
1. 将RabbitMQ连接到Adobe Commerce或Magento Open Source。

>[!NOTE]
>
>可以使用MySQL或RabbitMQ进行消息队列处理。 有关设置消息队列系统的详细信息，请参阅 [消息队列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/). 如果您将Bulk API与Adobe Commerce一起使用，则消息队列系统配置默认使用RabbitMQ作为消息代理。 请参阅 [启动消息队列使用者](../../configuration/cli/start-message-queues.md) 以了解更多信息。

## 在Ubuntu上安装RabbitMQ

要在Ubuntu 16上安装RabbitMQ，请输入以下命令：

```bash
sudo apt install -y rabbitmq-server
```

此命令还安装所需的Erlang包。

如果您的Ubuntu版本较旧，RabbitMQ建议从其网站安装该包。

1. 从下载.deb包 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. 使用 `dpkg`.

请参阅 [在Debian/Ubuntu上安装](https://www.rabbitmq.com/install-debian.html) 以了解更多信息。

## 在CentOS上安装RabbitMQ

### 安装Erlang

RabbitMQ是使用Erlang编程语言编写的，该语言必须安装在与RabbitMQ相同的系统上。

请参阅 [手动安装](https://www.erlang-solutions.com/downloads/) 以了解更多信息。

请参阅 [RabbitMQ/Erlang版本矩阵](https://www.rabbitmq.com/which-erlang.html) 以安装正确的版本。

### 安装RabbitMQ

RabbitMQ服务器包含在CentOS中，但版本通常为旧版本。 RabbitMQ建议从其网站安装包。

请参阅RabbitMQ安装页，获取支持的最新版本。 Adobe Commerce和Magento Open Source2.3和2.4支持RabbitMQ 3.8.x。

请参阅 [在基于RPM的Linux上安装](https://www.rabbitmq.com/install-rpm.html) 以了解更多信息。

## 配置RabbitMQ

查看官方的RabbitMQ文档以配置和管理RabbitMQ。 请注意以下事项：

* 环境变量
* 端口访问
* 默认用户帐户
* 启动和停止代理
* 系统限制

## 使用RabbitMQ安装并连接

如果安装Adobe Commerce或Magento Open Source _after_ 安装RabbitMQ时，请在安装过程中添加以下命令行参数：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

其中：

| 参数 | 描述 |
|--- |--- |
| `--amqp-host` | 安装RabbitMQ的主机名。 |
| `--amqp-port` | 用于连接到RabbitMQ的端口。 默认值为 `5672`. |
| `--amqp-user` | 用于连接到RabbitMQ的用户名。 请勿使用默认用户 `guest`. |
| `--amqp-password` | 用于连接到RabbitMQ的密码。 请勿使用默认密码 `guest`. |
| `--amqp-virtualhost` | 用于连接到RabbitMQ的虚拟主机。 默认值为 `/`. |
| `--amqp-ssl` | 指示是否连接到RabbitMQ。 默认值为 `false`. 如果将值设置为true，请参阅配置SSL以了解更多信息。 |

## 连接RabbitMQ

如果已安装Adobe Commerce或Magento Open Source，并且要将其连接到RabbitMQ，请添加 `queue` 部分 `<install_directory>/app/etc/env.php` 文件，以便其类似于以下内容：

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

您还可以使用 `bin/magento setup:config:set` 命令：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

运行命令或更新 `<install_directory>/app/etc/env.php` 文件，运行 `bin/magento setup:upgrade` 在RabbitMQ中应用更改并创建所需的队列和交换。

## 配置SSL

要配置对SSL的支持，请编辑 `ssl` 和 `ssl_options` 参数 `<install_directory>/app/etc/env.php` 文件，以便它们类似于以下内容：

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## 启动消息队列使用者

连接了Adobe Commerce和RabbitMQ后，必须启动消息队列用户。 请参阅 [配置消息队列](../../configuration/cli/start-message-queues.md) 以了解详细信息。
