---
title: 消息代理
description: 按照以下步骤安装和配置Adobe Commerce本地安装所需的消息代理软件（如 [!DNL RabbitMQ]）。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# 消息代理

Adobe Commerce使用[!DNL RabbitMQ]开源消息代理。 它提供可靠、高可用、可扩展且便携的消息传递系统。

消息队列提供了一种异步通信机制，在这种机制中，消息的发送者和接收者不会相互联系。 它们也不需要同时与消息队列通信。 当发件人将邮件放入队列时，该邮件会一直存储到收件人收到这些邮件为止。

安装Adobe Commerce之前，必须建立消息队列系统。 基本顺序为：

1. 安装[!DNL RabbitMQ]和任何先决条件。
1. 将[!DNL RabbitMQ]连接到Adobe Commerce。

>[!NOTE]
>
>您可以使用MySQL或[!DNL RabbitMQ]进行消息队列处理。 有关设置消息队列系统的详细信息，请参阅[消息队列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/)。 如果将Bulk API与Adobe Commerce一起使用，则消息队列系统配置默认为使用[!DNL RabbitMQ]作为消息代理。 有关详细信息，请参阅[启动消息队列使用者](../../configuration/cli/start-message-queues.md)。

## 在Ubuntu上安装[!DNL RabbitMQ]

要在Ubuntu 16上安装[!DNL RabbitMQ]，请输入以下命令：

```bash
sudo apt install -y rabbitmq-server
```

此命令还会安装所需的Erlang包。

如果您使用的是旧版本的Ubuntu，[!DNL RabbitMQ]建议从其网站安装包。

1. 从[rabbitmq-server](https://www.rabbitmq.com/download.html)下载.deb包。
1. 安装包含`dpkg`的包。

有关详细信息，请参阅[在Debian/Ubuntu上安装](https://www.rabbitmq.com/install-debian.html)。

## 在CentOS上安装[!DNL RabbitMQ]

### 安装Erlang

[!DNL RabbitMQ]是使用Erlang编程语言编写的，该语言必须安装在与[!DNL RabbitMQ]相同的系统上。

有关详细信息，请参阅[手动安装](https://www.erlang-solutions.com/downloads/)。

请参阅[[!DNL RabbitMQ]/Erlang版本矩阵](https://www.rabbitmq.com/which-erlang.html)以安装正确的版本。

### 安装[!DNL RabbitMQ]

[!DNL RabbitMQ]服务器包含在CentOS中，但版本通常较旧。 [!DNL RabbitMQ]建议从其网站安装包。

请参阅[!DNL RabbitMQ]安装页面以获取最新支持的版本。 Adobe Commerce 2.3和2.4支持[!DNL RabbitMQ] 3.8.x。

有关详细信息，请参阅[在基于RPM的Linux](https://www.rabbitmq.com/install-rpm.html)上安装。

## 配置[!DNL RabbitMQ]

查看官方[!DNL RabbitMQ]文档以配置和管理[!DNL RabbitMQ]。 请注意以下事项：

* 环境变量
* 端口访问
* 默认用户帐户
* 启动和停止代理
* 系统限制

## 使用[!DNL RabbitMQ]安装并连接

如果在安装&#x200B;_之后安装Adobe Commerce_，则在安装[!DNL RabbitMQ]期间添加以下命令行参数：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

其中：

| 参数 | 描述 |
|--- |--- |
| `--amqp-host` | 安装[!DNL RabbitMQ]的主机名。 |
| `--amqp-port` | 用于连接到[!DNL RabbitMQ]的端口。 默认值为`5672`。 |
| `--amqp-user` | 用于连接到[!DNL RabbitMQ]的用户名。 不要使用默认用户`guest`。 |
| `--amqp-password` | 用于连接到[!DNL RabbitMQ]的密码。 不要使用默认密码`guest`。 |
| `--amqp-virtualhost` | 用于连接到[!DNL RabbitMQ]的虚拟主机。 默认值为`/`。 |
| `--amqp-ssl` | 指示是否连接到[!DNL RabbitMQ]。 默认值为`false`。 如果将该值设置为true ，请参阅配置SSL以了解更多信息。 |

## 连接[!DNL RabbitMQ]

如果您已安装Adobe Commerce并且要将其连接到[!DNL RabbitMQ]，请在`queue`文件中添加`<install_directory>/app/etc/env.php`部分，以使其类似于以下内容：

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

您还可以使用[!DNL RabbitMQ]命令设置`bin/magento setup:config:set`配置值：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

运行命令或使用AMQP配置值更新`<install_directory>/app/etc/env.php`文件后，运行`bin/magento setup:upgrade`以应用更改并在[!DNL RabbitMQ]中创建所需的队列和交换。

## 配置SSL

要配置对SSL的支持，请编辑`ssl`文件中的`ssl_options`和`<install_directory>/app/etc/env.php`参数，使它们类似于以下内容：

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

连接Adobe Commerce和[!DNL RabbitMQ]后，必须启动消息队列使用者。 有关详细信息，请参阅[配置消息队列](../../configuration/cli/start-message-queues.md)。
