---
title: 消息代理
description: 按照以下步骤安装和配置所需的消息代理软件(例如 [!DNL RabbitMQ]Adobe Commerce )。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# 消息代理

Adobe Commerce使用 [!DNL RabbitMQ] 开源消息代理。 它提供可靠、高可用、可扩展且便携的消息传递系统。

消息队列提供了一种异步通信机制，在这种机制中，消息的发送者和接收者不会相互联系。 它们也不需要同时与消息队列通信。 当发件人将邮件放入队列时，该邮件会一直存储到收件人收到这些邮件为止。

安装Adobe Commerce之前，必须建立消息队列系统。 基本顺序为：

1. 安装 [!DNL RabbitMQ] 以及任何先决条件。
1. 连接 [!DNL RabbitMQ] Adobe Commerce。

>[!NOTE]
>
>您可以使用MySQL或 [!DNL RabbitMQ] 进行消息队列处理。 有关设置消息队列系统的详细信息，请参阅 [消息队列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/). 如果您要在Adobe Commerce中使用批量API，则消息队列系统配置默认为使用 [!DNL RabbitMQ] 作为消息代理。 请参阅 [启动消息队列使用者](../../configuration/cli/start-message-queues.md) 以了解更多信息。

## 安装 [!DNL RabbitMQ] 在Ubuntu

安装 [!DNL RabbitMQ] 在Ubuntu 16上，输入以下命令：

```bash
sudo apt install -y rabbitmq-server
```

此命令还会安装所需的Erlang包。

如果你有旧版的Ubuntu， [!DNL RabbitMQ] 建议从其网站安装包。

1. 从下载.deb包 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. 使用安装包 `dpkg`.

请参阅 [在Debian/Ubuntu上安装](https://www.rabbitmq.com/install-debian.html) 以了解更多信息。

## 安装 [!DNL RabbitMQ] 在CentOS上

### 安装Erlang

[!DNL RabbitMQ] 使用Erlang编程语言编写，该语言必须安装在与相同的系统上 [!DNL RabbitMQ].

请参阅 [手动安装](https://www.erlang-solutions.com/downloads/) 以了解更多信息。

请参阅 [[!DNL RabbitMQ]/Erlang版本列表](https://www.rabbitmq.com/which-erlang.html) 以安装正确的版本。

### 安装 [!DNL RabbitMQ]

此 [!DNL RabbitMQ] 服务器包含在CentOS中，但版本通常较旧。 [!DNL RabbitMQ] 建议从其网站安装包。

请参阅 [!DNL RabbitMQ] 安装页面，以获取支持的最新版本。 Adobe Commerce 2.3和2.4支持 [!DNL RabbitMQ] 3.8.x。

请参阅 [在基于rpm的Linux上安装](https://www.rabbitmq.com/install-rpm.html) 以了解更多信息。

## 配置 [!DNL RabbitMQ]

查看官方网站 [!DNL RabbitMQ] 配置和管理文档 [!DNL RabbitMQ]. 请注意以下事项：

* 环境变量
* 端口访问
* 默认用户帐户
* 启动和停止代理
* 系统限制

## 安装方式 [!DNL RabbitMQ] 并连接

如果您安装Adobe Commerce _之后_ 您安装 [!DNL RabbitMQ]中，在安装期间添加以下命令行参数：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

其中：

| 参数 | 描述 |
|--- |--- |
| `--amqp-host` | 主机名，其中 [!DNL RabbitMQ] 已安装。 |
| `--amqp-port` | 用于连接的端口 [!DNL RabbitMQ]. 默认为 `5672`. |
| `--amqp-user` | 用于连接到的用户名 [!DNL RabbitMQ]. 不使用默认用户 `guest`. |
| `--amqp-password` | 用于连接的密码 [!DNL RabbitMQ]. 不使用默认密码 `guest`. |
| `--amqp-virtualhost` | 用于连接的虚拟主机 [!DNL RabbitMQ]. 默认为 `/`. |
| `--amqp-ssl` | 指示是否连接到 [!DNL RabbitMQ]. 默认为 `false`. 如果将该值设置为true ，请参阅配置SSL以了解更多信息。 |

## 连接 [!DNL RabbitMQ]

如果您已安装Adobe Commerce并且希望将其连接到 [!DNL RabbitMQ]，添加 `queue` 中的部分 `<install_directory>/app/etc/env.php` 文件，以便它类似于以下内容：

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

您还可以设置 [!DNL RabbitMQ] 配置值使用 `bin/magento setup:config:set` 命令：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

运行命令或更新 `<install_directory>/app/etc/env.php` 文件和AMQP配置值，运行 `bin/magento setup:upgrade` 以应用更改并在中创建所需的队列和交换 [!DNL RabbitMQ].

## 配置SSL

要配置对SSL的支持，请编辑 `ssl` 和 `ssl_options` 中的参数 `<install_directory>/app/etc/env.php` 文件，以便它们类似于以下内容：

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

在连接Adobe Commerce和之后 [!DNL RabbitMQ]，则必须启动消息队列使用者。 请参阅 [配置消息队列](../../configuration/cli/start-message-queues.md) 以了解详细信息。
