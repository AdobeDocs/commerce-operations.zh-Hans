---
title: 高级内部部署安装
description: 了解Adobe Commerce内部部署的高级安装方案。 发现复杂的配置和自定义设置选项。
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 937db2209ec4122c611a857796f043523a0acb29
workflow-type: tm+mt
source-wordcount: '2485'
ht-degree: 0%

---

# 高级内部部署安装

>[!TIP]
>
>丢失？ 需要帮忙吗？ 尝试我们的[快速入门安装](composer.md)或[参与者安装](https://developer.adobe.com/commerce/contributor/guides/install/)指南。

>[!NOTE]
>
>如果您选择启用SELinux，请参阅[SELinux和iptables](prerequisites/security.md)。

## 命令行界面(CLI)

Adobe Commerce具有用于安装和配置任务的单个命令行界面： `<magento_root>/bin/magento`。 该界面可执行多项任务，包括：

* 安装（以及创建或更新数据库架构、创建部署配置等相关任务）。
* 正在清除缓存。
* 管理索引，包括重新编制索引。
* 创建翻译词典和翻译包。
* 为插件生成不存在的类（如工厂和侦听器），为对象管理器生成依赖项注入配置。
* 部署静态视图文件。
* 从更少内容创建CSS。

其他好处：

* 单个命令(`<magento_root>/bin/magento list`)列出了所有可用的安装和配置命令。
* 基于Symfony的一致用户界面。
* CLI是可扩展的，因此第三方开发人员可以“插入”到其中。 这还有消除用户学习曲线的额外好处。
* 禁用模块的命令不显示。

本主题讨论如何使用CLI安装Adobe Commerce软件。 有关配置的信息，请参阅[配置指南](../configuration/overview.md)。

如果需要，安装程序可以多次运行，这样您可以：

* 提供不同的值

  例如，在为Web服务器配置安全套接字层(SSL)后，可以运行安装程序来设置SSL选项。

* 更正以前安装中的错误
* 在其他数据库实例中安装Adobe Commerce

## 开始安装之前

在开始之前，请完成以下步骤：

* 验证您的系统是否符合[系统要求](system-requirements.md)中讨论的要求。

* 完成所有[必备项](prerequisites/overview.md)任务。

* 完成第一个安装步骤。 请参阅[您的安装或升级路径](overview.md)。

* 登录到应用程序服务器后，[切换到文件系统所有者](prerequisites/file-system/overview.md)。

* 查看[安装快速入门](composer.md)概述。

>[!NOTE]
>
>必须从`bin`子目录安装Adobe Commerce。

您可以使用不同的选项多次运行安装程序以完成如下安装任务：

* 分阶段安装 — 例如，在为Web服务器配置安全套接字层(SSL)后，可以再次运行安装程序以设置SSL选项。

* 更正以前安装中的错误。

* 在其他数据库实例中安装Adobe Commerce。

>[!NOTE]
>
>默认情况下，如果在同一数据库实例中安装软件，则安装程序不会覆盖数据库。 您可以使用可选的`cleanup-database`参数更改此行为。

另请参阅[更新、重新安装、卸载](tutorials/uninstall.md)。

### 安全安装

{{$include /help/_includes/secure-install.md}}

## 安装程序帮助命令

可以运行以下命令来查找某些所需参数的值：

| 安装程序参数 | 命令 |
| ------------------ | ------------------------------- |
| 语言 | `bin/magento info:language:list` |
| 货币 | `bin/magento info:currency:list` |
| 时区 | `bin/magento info:timezone:list` |

>[!NOTE]
>
>如果在运行这些命令时显示错误，请验证是否已按照[更新安装依赖项](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)中所述更新了安装依赖项。

## 从命令行安装

install命令使用以下格式：

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

下表描述了安装选项名称和值。 有关安装命令的示例，请参阅[示例localhost安装](#sample-localhost-installations)。

>[!NOTE]
>
>任何包含空格或特殊字符的选项都必须用单引号或双引号括起来。

**管理员凭据：**

以下选项指定管理员用户的用户信息和凭据。

您可以在安装期间或安装后创建管理员用户。 如果在安装期间创建用户，则需要所有管理员凭据变量。 请参阅[本地主机安装示例](#sample-localhost-installations)。

下表提供了许多而非所有可用的安装参数。 有关完整列表，请参阅[命令行工具引用](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises)。

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--admin-firstname` | 管理员用户的名字。 | 是 |
| `--admin-lastname` | 管理员用户的姓氏。 | 是 |
| `--admin-email` | 管理员用户的电子邮件地址。 | 是 |
| `--admin-user` | 管理员用户名。 | 是 |
| `--admin-password` | 管理员用户密码。 密码长度必须至少为7个字符，并且必须至少包含一个字母和至少一个数字字符。 我们建议使用更长、更复杂的密码。 用单引号将整个密码字符串括起来。 例如，`--admin-password='A0b9%t3g'` | 是 |

**站点和数据库配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--base-url` | 用于以下列任何格式访问管理员和店面的基本URL：<br><br>`http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：**&#x200B;方案(http://或https://)和尾随斜杠都是必需的。<br><br>`<your install dir>`是安装Adobe Commerce软件的docroot相对路径。 根据您设置Web服务器和虚拟主机的方式，路径可能是magento2或为空。<br><br>访问Adobe Commerce或MagenAdobe Commerceuse `http://127.0.0.1/<your install dir>/`或`http://127.0.0.1/<your install dir>/`。<br><br>- `{{base_url}}`，表示由虚拟主机设置或Docker等虚拟化环境定义的基本URL。 例如，如果您设置了主机名为`magento.example.com`的虚拟主机，则可以使用`--base-url={{base_url}}`安装软件，并使用类似`http://magento.example.com/admin`的URL访问管理员。 | 是 |
| `--backend-frontname` | 用于访问管理员的统一资源标识符(URI)。 您可以忽略此参数，以便应用程序使用以下模式为您生成随机URI <code>admin_jkhgdfq</code>。<br><br>出于安全考虑，我们建议使用随机URI。 黑客或恶意软件更难利用随机URI。<br><br>URI显示在安装结束时。 您可以稍后随时使用`bin/magento info:adminuri`命令显示它。<br><br>如果您选择输入值，我们建议您不要使用诸如admin、backend之类的常用词。 管理员URI只能包含字母数字值和下划线字符(`_`)。 | 否 |
| `--db-host` | 使用以下任一项：<br><br> — 数据库服务器的完全限定主机名或IP地址。<br><br>- `localhost`（默认）或`127.0.0.1`（如果数据库服务器与Web服务器位于同一主机上）。localhost表示MySQL客户端库使用UNIX套接字连接到数据库。 `127.0.0.1`导致客户端库使用TCP协议。 有关套接字的详细信息，请参阅[PHP PDO_MYSQL文档](https://www.php.net/manual/en/ref.pdo-mysql.php)。<br><br>**注意：**&#x200B;您可以选择在其主机名中指定数据库服务器端口，如www.example.com:9000 | 是 |
| `--db-name` | 要在其中安装数据库表的数据库实例的名称。<br><br>默认值为`magento2`。 | 是 |
| `--db-user` | 数据库实例所有者的用户名。<br><br>默认值为`root`。 | 是 |
| `--db-password` | 数据库实例所有者的密码。 | 是 |
| `--db-prefix` | 仅当在已有Adobe Commerce表的数据库实例中安装数据库表时才使用。<br><br>在这种情况下，请使用前缀来标识此安装的表。 某些客户有多个Adobe Commerce或MagenAdobe Commerceserver，在同一数据库中包含所有表。<br><br>前缀长度最多可为5个字符。 它必须以字母开头，并且只能包含字母、数字和下划线字符。<br><br>此选项使这些客户能够与多个Adobe Commerce安装共享数据库服务器 |
| `--db-ssl-key` | 客户端密钥的路径。 | 否 |
| `--db-ssl-cert` | 客户端证书的路径。 | 否 |
| `--db-ssl-ca` | 服务器证书的路径。 | 否 |
| `--language` | 在管理员和店面中使用的语言代码。 （如果尚未这样做，则可以通过输入bin目录中的`bin/magento info:language:list`来查看语言代码列表。） | 否 |
| `--currency` | 店面中使用的默认货币。 （如果尚未这样做，则可以通过输入bin目录中的`bin/magento info:currency:list`来查看货币列表。） | 否 |
| `--timezone` | 在管理员和店面中使用的默认时区。 （如果您尚未这样做，则可以通过输入`bin/magento info:timezone:list`目录中的`bin/`来查看时区列表。） | 否 |
| `--use-rewrites` | `1`表示您对店面和管理中生成的链接使用Web服务器重写。<br><br>`0`禁用使用Web服务器重写。 这是默认设置。 | 否 |
| `--use-secure` | `1`允许在店面URL中使用安全套接字层(SSL)。 在选择此选项之前，请确保您的Web服务器支持SSL。<br><br>`0`禁用使用SSL。 在这种情况下，所有其他安全URL选项也假定为0。 这是默认设置。 | 否 |
| `--base-url-secure` | 用于访问管理员和店面的安全基础URL，格式如下： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1`表示您使用SSL访问管理员。 在选择此选项之前，请确保您的Web服务器支持SSL。<br><br>`0`表示您未将SSL与管理员一起使用。 这是默认设置。 | 否 |
| `--admin-use-security-key` | 1导致应用程序使用随机生成的键值来访问管理员和表单中的页面。 这些键值有助于防止跨站点脚本伪造攻击。 这是默认设置。<br><br>`0`禁用该密钥。 | 否 |
| `--session-save` | 使用以下任意一项： <br><br>- `db`将会话数据存储到数据库中。 如果您有群集数据库，请选择数据库存储；否则，与基于文件的存储相比，这样做可能没有多大好处。<br><br>- `files`以在文件系统中存储会话数据。 基于文件的会话存储是合适的，除非文件系统访问速度较慢，或者您拥有集群数据库，或者希望将会话数据存储在Redis中。<br><br>- `redis`在Redis中存储会话数据。 如果将Redis用于默认缓存或页面缓存，则必须已安装Redis。 有关配置对Redis的支持的其他信息，请参阅将Redis用于会话存储。 | 否 |
| `--key` | 如果您有密钥，请指定密钥以加密数据库中的敏感数据。 如果您没有，应用程序将为您生成一个。 | 是 |
| `--cleanup-database` | 要在安装Adobe Commerce之前删除数据库表，请指定此参数，而不使用值。 否则，数据库将保持不变。 | 否 |
| `--db-init-statements` | 高级MySQL配置参数。 在连接到MySQL数据库时使用数据库初始化语句运行。 在设置任何值之前，请查阅与此类似的引用。<br><br>默认值为`SET NAMES utf8;`。 | 否 |
| `--sales-order-increment-prefix` | 指定要用作销售订单前缀的字符串值。 通常，这用于保证支付处理者的唯一订单编号。 | 否 |

**搜索引擎配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--search-engine` | 用作搜索引擎的Elasticsearch或OpenSearch的版本。 默认值为`elasticsearch7`。 Elasticsearch 5已被弃用，不建议使用。 | 否 |
| `--elasticsearch-host` | 运行Elasticsearch的主机名或IP地址。 默认值为`localhost`。 | 否 |
| `--elasticsearch-port` | 用于传入HTTP请求的Elasticsearch端口。 默认值为`9200`。 | 否 |
| `--elasticsearch-index-prefix` | 标识Elasticsearch搜索索引的前缀。 默认值为`magento2`。 | 否 |
| `--elasticsearch-timeout` | 系统超时前的秒数。 默认值为`15`。 | 否 |
| `--elasticsearch-enable-auth` | 在Elasticsearch服务器上启用身份验证。 默认值为`false`。 | 否 |
| `--elasticsearch-username` | 用于向Elasticsearch服务器进行身份验证的用户ID。 | 否，除非启用身份验证 |
| `--elasticsearch-password` | 用于向Elasticsearchserver进行验证的密码。 | 否，除非启用身份验证 |
| `--opensearch-host` | 运行OpenSearch的主机名或IP地址。 默认值为`localhost`。 | 否 |
| `--opensearch-port` | 用于传入HTTP请求的OpenSearch端口。 默认值为`9200`。 | 否 |
| `--opensearch-index-prefix` | 标识OpenSearch搜索索引的前缀。 默认值为`magento2`。 | 否 |
| `--opensearch-timeout` | 系统超时前的秒数。 默认值为`15`。 | 否 |
| `--opensearch-enable-auth` | 在OpenSearch服务器上启用身份验证。 默认值为`false`。 | 否 |
| `--opensearch-username` | 用于向OpenSearch服务器进行身份验证的用户ID。 | 否，除非启用身份验证 |
| `--opensearch-password` | 用于向OpenSearch服务器进行身份验证的密码。 | 否，除非启用身份验证 |

**[!DNL RabbitMQ]配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--amqp-host` | 请勿使用`--amqp`选项，除非您已设置[!DNL RabbitMQ]的安装。 有关安装和配置[!DNL RabbitMQ]的详细信息，请参阅[!DNL RabbitMQ]安装。<br><br>安装[!DNL RabbitMQ]的主机名。 | 否 |
| `--amqp-port` | 用于连接到[!DNL RabbitMQ]的端口。 默认值为5672。 | 否 |
| `--amqp-user` | 用于连接到[!DNL RabbitMQ]的用户名。 不要使用默认用户`guest`。 | 否 |
| `--amqp-password` | 用于连接到[!DNL RabbitMQ]的密码。 不要使用默认密码`guest`。 | 否 |
| `--amqp-virtualhost` | 用于连接到[!DNL RabbitMQ]的虚拟主机。 默认值为`/`。 | 否 |
| `--amqp-ssl` | 指示是否连接到[!DNL RabbitMQ]。 默认值为`false`。 有关为[!DNL RabbitMQ]设置SSL的信息，请参阅[!DNL RabbitMQ]。 | 否 |
| `--consumers-wait-for-messages` | 消费者是否应该等待队列中的消息？ 1 — 是，0 — 否 | 否 |

**ActiveMQ Artemis配置选项：**

>[!NOTE]
>
>ActiveMQ Artemis在Adobe Commerce 2.4.6及更高版本中引入。

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--stomp-host` | 请勿使用`--stomp`选项，除非您已设置ActiveMQ Artemis的安装。 有关安装和配置ActiveMQ Artemis的详细信息，请参阅ActiveMQ Artemis安装。<br><br>安装ActiveMQ Artemis的主机名。 | 否 |
| `--stomp-port` | 用于连接到ActiveMQ Artemis的端口。 默认值为61613。 | 否 |
| `--stomp-user` | 用于连接到ActiveMQ Artemis的用户名。 不要使用默认用户`artemis`。 | 否 |
| `--stomp-password` | 用于连接到ActiveMQ Artemis的密码。 不要使用默认密码`artemis`。 | 否 |
| `--stomp-ssl` | 指示是否使用SSL连接到ActiveMQ Artemis。 默认值为`false`。 有关为ActiveMQ项目设置SSL的信息，请参阅ActiveMQ项目。 | 否 |
| `--consumers-wait-for-messages` | 消费者是否应该等待队列中的消息？ 1 — 是，0 — 否 | 否 |

**锁定配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--lock-provider` | 锁定提供程序名称。<br><br>可用的锁定提供程序： `db`、`zookeeper`、`file`。<br><br>默认锁定提供程序： `db` | 否 |
| `--lock-db-prefix` | 使用`db`锁定提供程序时为避免锁定冲突而使用的特定数据库前缀。<br><br>默认值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用`zookeeper`锁定提供程序时用于连接到Zookeeper群集的主机和端口。<br><br>例如： `127.0.0.1:2181` | 是，如果您设置`--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存锁的路径。<br><br>默认路径为： `/magento/locks` | 否 |
| `--lock-file-path` | 保存文件锁定的路径。 | 是，如果您设置`--lock-provider=file` |

**使用者配置选项：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>要在安装Adobe Commerce后启用或禁用模块，请参阅[启用和禁用模块](tutorials/manage-modules.md)。

**敏感数据：**

{{$include /help/_includes/sensitive-data.md}}

### localhost安装示例

以下示例显示了使用各种选项在本地安装Adobe Commerce的命令。

#### 示例1 — 使用管理员用户帐户进行基本安装

以下示例使用下列选项安装Adobe Commerce：

* 该应用程序安装在`magento2`上相对于Web服务器docroot的`localhost`目录中，并且管理员的路径为`admin`；因此：

  您的店面URL是`http://127.0.0.1`

* 数据库服务器与Web服务器位于同一主机上。

  数据库名称为`magento`，用户名和密码均为`magento`

* 使用服务器重写

* 管理员具有以下属性：

   * 名字和姓氏是`Magento User`
   * 用户名是`admin`，密码是`admin123`
   * 电子邮件地址为`user@example.com`

* 默认语言为`en_US` （美国英语）
* 默认货币为美元
* 默认时区为美国中部（美洲/芝加哥）
* OpenSearch 1.2安装在`os-host.example.com`上并连接到端口9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

类似于以下内容的消息显示指示安装成功：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 示例2 — 无管理员用户帐户的基本安装

您可以安装Adobe Commerce而不创建管理员用户，如以下示例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

如果安装成功，将显示如下消息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安装后，您可以使用`admin:user:create`命令创建管理员用户：
[创建或编辑管理员](tutorials/admin.md#create-or-edit-an-administrator)

#### 示例3 — 使用其他选项进行安装

以下示例使用下列选项安装Adobe Commerce：

* 该应用程序安装在`magento2`上相对于Web服务器docroot的`localhost`目录中，并且管理员的路径为`admin`；因此：

  您的店面URL是`http://127.0.0.1`

* 数据库服务器与Web服务器位于同一主机上。

  数据库名称为`magento`，用户名和密码均为`magento`

* 管理员具有以下属性：

   * 名字和姓氏是`Magento User`
   * 用户名是`admin`，密码是`admin123`
   * 电子邮件地址为`user@example.com`

* 默认语言为`en_US` （美国英语）
* 默认货币为美元
* 默认时区为美国中部（美洲/芝加哥）
* 安装程序先清理数据库，然后再安装表和模式
* 您可以使用销售订单增量前缀`ORD$`（由于它包含特殊字符[`$`]，因此必须将值用双引号括起来）
* 会话数据保存在数据库中
* 使用服务器重写
* OpenSearch安装在`os-host.example.com`上并连接到端口9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>您必须在单行中输入命令，或者如上例所示，在每行末尾输入`\`字符。

如果安装成功，将显示如下消息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 示例4 — 使用ActiveMQ Artemis安装

以下示例说明如何将Adobe Commerce与作为消息代理的ActiveMQ Artemis一起安装：

```bash
bin/magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>ActiveMQ Artemis安装需要Adobe Commerce 2.4.6或更高版本。

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
