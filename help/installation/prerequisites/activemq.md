---
title: 消息代理(ActiveMQ Artemis)
description: 按照以下步骤为Adobe Commerce的内部安装安装和配置Apache ActiveMQ Artemis消息代理。
source-git-commit: aee02c258acaeb7a248e10b867017ef8f72b544d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# 消息代理(ActiveMQ Artemis)

Adobe Commerce还通过简单文本导向消息协议(STOMP)支持ActiveMQ Artemis开源消息代理。 它提供了可靠且可扩展的报文传送系统，为基于STOMP的集成提供了灵活性。


>[!NOTE]
>
>ActiveMQ Artemis在Adobe Commerce 2.4.6及更高版本中引入。 有关在云基础架构项目上的Adobe Commerce中安装ActiveMQ Artemis的详细信息，请参阅《云上的Commerce指南》[中的](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/service/activemq)设置ActiveMQ服务&#x200B;**。

消息队列提供了一种异步通信机制，在这种机制中，消息的发送者和接收者不会相互联系。 它们也不需要同时与消息队列通信。 当发件人将邮件放入队列时，该邮件会一直存储到收件人收到这些邮件为止。

安装Adobe Commerce之前，必须建立消息队列系统。 基本顺序为：

1. 安装Apache ActiveMQ Artemis和任何先决条件。
1. 将ActiveMQ连接到Adobe Commerce。

>[!NOTE]
>
>您可以使用MySQL、ActiveMQ或[!DNL RabbitMQ]进行消息队列处理。 有关设置消息队列系统的详细信息，请参阅[消息队列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/)。 如果将Bulk API与Adobe Commerce一起使用，则消息队列系统配置默认为使用[!DNL RabbitMQ]作为消息代理。 有关详细信息，请参阅[启动消息队列使用者](../../configuration/cli/start-message-queues.md)。

>[!TIP]
>
>在安装之前，请始终检查[Apache ActiveMQ Artemis下载页面](https://activemq.apache.org/components/artemis/download/)中的最新稳定版本。 本文档中的示例使用的是版本2.42.0，这是截至2025年9月的最新稳定版本。


## 安装Apache ActiveMQ Artemis

您可以使用Docker（建议用于开发）或手动安装（建议用于生产）来安装ActiveMQ Artemis。

### 选项1：Docker安装（建议用于开发）

#### 先决条件

确保在系统上安装并运行Docker。

>[!TIP]
>
>有关官方ActiveMQ Artemis Docker映像的详细信息，请参阅[Apache ActiveMQ Artemis Docker中心页面](https://hub.docker.com/r/apache/activemq-artemis)。

#### 安装步骤

1. 使用官方的Docker映像运行ActiveMQ Artemis：

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. 使用自定义凭据运行：

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Docker管理命令

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### 访问服务

运行Docker容器后，您可以访问：

- **Web控制台**： http://localhost:8161/控制台（默认凭据： artemis/artemis）
- **STOMP端口**： localhost:61613 (用于Adobe Commerce连接)

>[!NOTE]
>
>建议将Docker安装用于开发和测试。 对于生产，请考虑使用具有适当安全配置的手动安装。

### 选项2：在Ubuntu/CentOS上手动安装

#### 先决条件

确保安装了Java 17或更高版本（ActiveMQ Artemis 2.42.0+要求）。

### 安装步骤

1. 从[Apache ActiveMQ Artemis网站](https://activemq.apache.org/components/artemis/download/)下载并安装最新版本。 截至2025年9月，最新稳定版本为2.42.0：

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. 创建`artemis`用户并设置所有权：

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. 创建Broker实例：

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. 启动代理：

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## 配置ActiveMQ Artemis

查看官方ActiveMQ Artemis文档以配置和管理代理。 请注意以下事项：

- 环境变量
- 端口访问（STOMP协议）
- 默认用户帐户和凭据
- 启动和停止代理
- 系统限制和资源调整

### 关键配置文件

- `/var/lib/artemis-instance/etc/broker.xml` — 主代理配置
- `/var/lib/artemis-instance/etc/artemis-users.properties` — 用户身份验证
- `/var/lib/artemis-instance/etc/artemis-roles.properties` — 用户角色
- `/var/lib/artemis-instance/etc/bootstrap.xml` — 配置Bootstrap

### 启用STOMP协议

检查`/var/lib/artemis-instance/etc/broker.xml`以确保已配置STOMP接受器：

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

要在STOMP上启用SSL，必须显式添加`stomp-ssl`接受方。

## 使用ActiveMQ Artemis安装并连接

如果在安装ActiveMQ Artemis _之后安装Adobe Commerce_，请在安装期间添加以下命令行参数：

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

其中：

| 参数 | 描述 |
|--- |--- |
| `--stomp-host` | 安装ActiveMQ的主机名。 |
| `--stomp-port` | 用于连接到ActiveMQ的端口。 默认值为`61613`。 |
| `--stomp-user` | 用于连接到ActiveMQ的用户名。 不要使用默认用户`artemis`。 |
| `--stomp-password` | 用于连接到ActiveMQ的密码。 不要使用默认密码`artemis`。 |
| `--stomp-ssl` | 指示是否连接到ActiveMQ。 默认值为`false`。 如果将该值设置为true ，请参阅配置SSL以了解更多信息。 |

## 连接ActiveMQ Artemis

如果您在`<install_directory>/app/etc/env.php`文件中已有使用RabbitMQ (AMQP)配置的Adobe Commerce实例，并且要将其连接到ActiveMQ，请将`queue`部分替换为STOMP，以使其类似于以下内容：

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

您还可以使用`bin/magento setup:config:set`命令设置ActiveMQ配置值（如果`app/etc/env.php`文件中存在AMQP配置，请将其删除）：

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

运行命令或使用STOMP配置值更新`<install_directory>/app/etc/env.php`文件后，运行`bin/magento setup:upgrade`以应用更改并在ActiveMQ中创建所需的队列。

## 配置SSL

要配置对SSL的支持，请编辑`ssl`文件中的`ssl_options`和`<install_directory>/app/etc/env.php`参数，使它们类似于以下内容：

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### ssl配置选项

| 选项 | 描述 | 默认 |
|--- |--- |--- |
| `verify_peer` | 验证代理的SSL证书 | `true` |
| `verify_peer_name` | 验证代理的主机名是否与证书匹配 | `true` |
| `allow_self_signed` | 允许自签名证书 | `false` |
| `cafile` | 用于代理验证的CA证书文件的路径 | SSL必需 |
| `certfile` | 客户端证书文件的路径（用于双向SSL） | 可选 |
| `keyfile` | 客户端私钥文件的路径（用于双向SSL） | 可选 |
| `passphrase` | 客户端私钥密码 | 可选 |

### 开发SSL配置

对于开发环境，您可以使用宽松的SSL设置：

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## 性能调整

ActiveMQ Artemis提供了多个性能调整选项：

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## 监控和管理

### Web控制台

ActiveMQ Artemis提供了一个基于Web的管理控制台，可从以下位置访问：
- URL： `http://localhost:8161/console`
- 默认凭据： `artemis/artemis`

## 故障排除

### 常见问题

1. **连接被拒绝**：确保ActiveMQ Artemis正在运行并且配置了STOMP接受器。
1. **身份验证失败**：在Broker配置和`env.php`文件中检查用户名/密码。
1. **SSL握手失败**：验证SSL证书和配置。




### 验证STOMP连接

使用telnet测试STOMP连接：

```bash
telnet localhost 61613
```

您应该会看到连接已建立。 使用STOMP命令进行测试：

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

预期输出应显示已建立的连接和STOMP协议响应。

## 启动消息队列使用者

连接Adobe Commerce和ActiveMQ Artemis后，必须启动消息队列使用者。 有关详细信息，请参阅[配置消息队列](../../configuration/cli/start-message-queues.md)。

