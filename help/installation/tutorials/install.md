---
title: 安装Adobe Commerce
description: 按照以下步骤在您拥有的基础架构上安装Adobe Commerce或Magento Open Source。
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---


# 安装Adobe Commerce

在开始之前，请完成以下步骤：

* 验证您的系统是否满足 [系统要求](../system-requirements.md).

* 全部完成 [先决条件](../prerequisites/overview.md) 任务。

* 完成第一个安装步骤。 请参阅 [您的安装或升级路径](../overview.md).

* 登录到应用程序服务器后， [切换到文件系统所有者](../prerequisites/file-system/overview.md).

* 查看 [命令行安装入门](../composer.md) 概述。

>[!NOTE]
>
>必须从 `bin` 子目录。

您可以使用不同的选项多次运行安装程序以完成如下安装任务：

* 分阶段安装 — 例如，在为安全套接字层(SSL)配置Web服务器后，可以再次运行安装程序以设置SSL选项。

* 更正以前安装中的错误。

* 在其他数据库实例中安装应用程序。

>[!NOTE]
>
>默认情况下，如果在同一数据库实例中安装商务软件，则安装程序不会覆盖数据库。 您可以使用可选 `cleanup-database` 参数来更改此行为。

另请参阅 [更新、重新安装、卸载](uninstall.md).

## 安全安装

{{$include /help/_includes/secure-install.md}}

## 安装程序帮助命令

您可以运行以下命令来查找某些必需参数的值：

| 安装程序参数 | 命令 |
| ------------------ | ------------------------------- |
| 语言 | `magento info:language:list` |
| 货币 | `magento info:currency:list` |
| 时区 | `magento info:timezone:list` |

>[!NOTE]
>
>如果运行这些命令时显示错误，请验证是否按照 [更新安装依赖项](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 从命令行安装

安装命令使用以下格式：

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

下表描述了安装选项的名称和值，如安装命令。 请参阅 [本地主机安装示例](#sample-localhost-installations).

>[!NOTE]
>
>任何包含空格或特殊字符的选项都必须用单引号或双引号括起来。

**管理员凭据：**

以下选项指定管理员用户的用户信息和凭据。

在Adobe Commerce版本2.2.8及更高版本中，您可以在安装期间或安装后创建管理员用户。 如果在安装期间创建用户，则需要所有管理员凭据变量。 请参阅 [本地主机安装示例](#sample-localhost-installations).

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--admin-firstname` | 管理员用户的名字。 | 是 |
| `--admin-lastname` | 管理员用户的姓氏。 | 是 |
| `--admin-email` | 管理员用户的电子邮件地址。 | 是 |
| `--admin-user` | 管理员用户名。 | 是 |
| `--admin-password` | 管理员用户密码。 密码长度必须至少为7个字符，并且必须至少包含一个字母和一个数字字符。 我们建议使用更长、更复杂的密码。 用单引号引住整个密码字符串。 例如，`--admin-password='A0b9%t3g'` | 是 |

**站点和数据库配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--base-url` | 用于以下任何格式访问管理员和店面的基本URL:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** 方案(http://或https://)和尾随斜杠都是必需的。<br><br>`<your install dir>` 是安装应用程序的相对路径。 根据您设置Web服务器和虚拟主机的方式，路径可能为magento2或为空。<br><br>要在localhost上访问应用程序，可以使用 `http://127.0.0.1/<your install dir>/` 或 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 它表示由虚拟主机设置或由诸如Docker之类的虚拟化环境定义的基本URL。 例如，如果您使用主机名commerce.example.com设置虚拟主机，则可以使用 `--base-url={{base_url}}` 并使用之类的URL访问管理员 `http://commerce.example.com/admin`. | 是 |
| `--backend-frontname` | 统一资源标识符(URI)以访问管理员。 您可以忽略此参数，以便让应用程序使用以下模式为您生成随机URI:admin_jkhgdfq</code>.<br><br>出于安全考虑，我们建议使用随机URI。 随机URI对黑客或恶意软件来说更难以利用。<br><br>URI在安装结束时显示。 您可以随时使用 `magento info:adminuri` 命令。<br><br>如果您选择输入值，我们建议您不要使用“管理员”、“后端”等常用词语。 管理员URI可以包含字母数字值和下划线字符(`_`)。 | 否 |
| `--db-host` | 使用以下任一方法：<br><br> — 数据库服务器的完全限定的主机名或IP地址。<br><br>- `localhost` （默认）或 `127.0.0.1` 如果数据库服务器与web server.localhost位于同一主机上，则表示MySQL客户端库使用UNIX套接字连接到数据库。 `127.0.0.1` 导致客户端库使用TCP协议。 有关套接字的详细信息，请参阅 [PHP PDO_MYSQL文档](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** 您可以选择在其主机名中指定数据库服务器端口，如www.example.com:9000 | 是 |
| `--db-name` | 要在其中安装数据库表的数据库实例的名称。<br><br>默认为 `magento2`. | 是 |
| `--db-user` | 数据库实例所有者的用户名。<br><br>默认为 `root`. | 是 |
| `--db-password` | 数据库实例所有者的密码。 | 是 |
| `--db-prefix` | 仅当要在已具有Adobe Commerce或Magento Open Source表的数据库实例中安装数据库表时，才使用。<br><br>在这种情况下，请使用前缀来标识此安装的表。 某些客户在服务器上运行了多个Adobe Commerce和Magento Open Source实例，且所有表都位于同一数据库中。<br><br>前缀长度最多可为5个字符。 它必须以字母开头，并且只能包含字母、数字和下划线字符。<br><br>此选项使这些客户能够共享具有多个安装的数据库服务器。 | 否 |
| `--db-ssl-key` | 客户端密钥的路径。 | 否 |
| `--db-ssl-cert` | 客户端证书的路径。 | 否 |
| `--db-ssl-ca` | 服务器证书的路径。 | 否 |
| `--language` | 要在管理员和店面中使用的语言代码。 (如果尚未这样做，则可通过输入 `magento info:language:list` 从bin目录。) | 否 |
| `--currency` | 在店面中使用的默认货币。 (如果您尚未这样做，则可以通过输入 `magento info:currency:list` 从bin目录。) | 否 |
| `--timezone` | 在管理员和店面中使用的默认时区。 (如果您尚未这样做，则可以通过输入 `magento info:timezone:list` 从bin目录。) | 否 |
| `--use-rewrites` | `1` 表示您对storefront和“管理员”中生成的链接使用web服务器重写。<br><br>`0` 禁用web服务器重写的使用。 这是默认设置。 | 否 |
| `--use-secure` | `1` 允许在店面URL中使用安全套接字层(SSL)。 在选择此选项之前，请确保Web服务器支持SSL。<br><br>`0` 禁用SSL的使用。 在这种情况下，所有其他安全URL选项也被假定为0。 这是默认设置。 | 否 |
| `--base-url-secure` | 安全基本URL，用于以下格式访问管理员和店面： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 表示您使用SSL访问管理员。 在选择此选项之前，请确保Web服务器支持SSL。<br><br>`0` 表示您不将SSL与管理员一起使用。 这是默认设置。 | 否 |
| `--admin-use-security-key` | 1会导致应用程序使用随机生成的键值访问管理员和表单中的页面。 这些键值有助于防止跨站点脚本伪造攻击。 这是默认设置。<br><br>`0` 禁用键的使用。 | 否 |
| `--session-save` | 使用以下任一方法：<br><br>- `db` 用于在数据库中存储会话数据。 如果您有群集数据库，请选择数据库存储；否则，与基于文件的存储相比，可能没有太大的好处。<br><br>- `files` 用于在文件系统中存储会话数据。 基于文件的会话存储是适当的，除非文件系统访问速度慢、您有群集数据库，或者您希望在Redis中存储会话数据。<br><br>- `redis` 用于在Redis中存储会话数据。 如果您使用Redis进行默认缓存或页面缓存，则必须已安装Redis。 有关配置对Redi的支持的其他信息，请参阅使用Redis进行会话存储。 | 否 |
| `--key` | 如果您有密钥，请指定一个密钥以加密数据库中的敏感数据。 如果您没有，则应用程序会为您生成一个。 | 是 |
| `--cleanup-database` | 要在安装应用程序之前删除数据库表，请指定此参数，但不带值。 否则，数据库将保持不变。 | 否 |
| `--db-init-statements` | 高级MySQL配置参数。 使用数据库初始化语句在连接到MySQL数据库时运行。 在设置任何值之前，请参考与此类似的引用。<br><br>默认为 `SET NAMES utf8;`. | 否 |
| `--sales-order-increment-prefix` | 指定用作销售订单前缀的字符串值。 通常，它用于保证支付处理者的唯一订单号。 | 否 |

>[!TIP]
>
>要在安装过程中启用远程存储服务，请参阅 [配置远程存储](../../configuration/remote-storage/remote-storage.md) 在 _配置指南_.

**搜索引擎配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--search-engine` | 搜索引擎的版本。 可能的值为 `elasticsearch7`, `elasticsearch6`和 `elasticsearch5`. 默认值为 `elasticsearch7`. 如果已将OpenSearch安装为搜索引擎，请指定值 `elasticsearch7`. Elasticsearch5已弃用，不建议使用。 | 否 |
| `--elasticsearch-host` | 搜索引擎运行的主机名或IP地址。 默认值为 `localhost`. | 否 |
| `--elasticsearch-port` | 传入HTTP请求的端口。 默认值为 `9200`. | 否 |
| `--elasticsearch-index-prefix` | 标识搜索索引的前缀。 默认值为 `magento2`. | 否 |
| `--elasticsearch-timeout` | 系统超时前的秒数。 默认值为 `15`. | 否 |
| `--elasticsearch-enable-auth` | 在搜索引擎服务器上启用身份验证。 默认值为 `false`. | 否 |
| `--elasticsearch-username` | 要验证的用户ID | 否，除非启用了身份验证 |
| `--elasticsearch-password` | 验证密码 | 否，除非启用了身份验证 |

**RabbitMQ配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--amqp-host` | 请勿使用 `--amqp` 选项，除非您已设置RabbitMQ的安装。 有关安装和配置RabbitMQ的详细信息，请参阅RabbitMQ安装。<br><br>安装RabbitMQ的主机名。 | 否 |
| `--amqp-port` | 用于连接到RabbitMQ的端口。 默认为5672。 | 否 |
| `--amqp-user` | 用于连接到RabbitMQ的用户名。 请勿使用默认用户 `guest`. | 否 |
| `--amqp-password` | 用于连接到RabbitMQ的密码。 请勿使用默认密码 `guest`. | 否 |
| `--amqp-virtualhost` | 用于连接到RabbitMQ的虚拟主机。 默认值为 `/`. | 否 |
| `--amqp-ssl` | 指示是否连接到RabbitMQ。 默认值为 `false`. 有关为RabbitMQ设置SSL的信息，请参阅RabbitMQ 。 | 否 |
| `--consumers-wait-for-messages` | 消费者是否应等待队列中的消息？ 1 — 是，0 — 否 | 否 |

**远程存储选项：**

| 名称 | 描述 | 必需？ |
|--- |--- |--- |
| `remote-storage-driver` | 适配器名称<br>可能值：<br>**文件**:禁用远程存储并使用本地文件系统&#x200B;<br>**aws-s3**:使用 [Amazon Simple Storage Service(Amazon S3)](https://aws.amazon.com/s3/) | 否 |
| `remote-storage-bucket` | 对象存储或容器名称 | 否 |
| `remote-storage-prefix` | 可选前缀（对象存储内的位置） | 否 |
| `remote-storage-region` | 区域名称 | 否 |
| `remote-storage-key` | 可选访问密钥 | 否 |
| `remote-storage-secret` | 可选密钥 | 否 |

**锁定配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--lock-provider` | 锁定提供程序名称。<br><br>可用的锁定提供程序： `db`, `zookeeper`, `file`.<br><br>默认的锁定提供程序： `db` | 否 |
| `--lock-db-prefix` | 用于避免在使用 `db` 锁定提供程序。<br><br>默认值： `NULL` | 否 |
| `--lock-zookeeper-host` | 在使用 `zookeeper` 锁定提供程序。<br><br>例如： `127.0.0.1:2181` | 是，如果您设置 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存锁的路径。<br><br>默认路径为： `/magento/locks` | 否 |
| `--lock-file-path` | 保存文件锁定的路径。 | 是，如果您设置 `--lock-provider=file` |

**消费者配置选项：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>要在安装应用程序后启用或禁用模块，请参阅 [启用和禁用模块](manage-modules.md).

**敏感数据：**

{{$include /help/_includes/sensitive-data.md}}

### 本地主机安装示例

以下示例显示了使用各种选项在本地安装Adobe Commerce的命令。

#### 示例1 — 使用管理员用户帐户进行基本安装

以下示例安装具有以下选项的应用程序：

* 应用程序安装在 `magento2` 与web服务器docroot相关的目录 `localhost` 而管理员的路径是 `admin`;因此：

   您的店面URL是 `http://127.0.0.1`

* 数据库服务器与Web服务器位于同一主机上。

   数据库名称为 `magento`，且用户名和密码均为 `magento`

* 使用服务器重写

* 管理员具有以下属性：

   * 名字和姓氏为 `Commerce User`
   * 用户名为 `admin` 密码是 `admin123`
   * 电子邮件地址为 `user@example.com`

* 默认语言为 `en_US` （美国英语）
* 默认货币为美元
* 默认时区为“美国中部”（美国/芝加哥）
* Elasticsearch7安装在 `es-host.example.com` 并连接端口9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

与以下显示类似的消息，用于指示安装成功：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 示例2 — 在没有管理员用户帐户的情况下进行基本安装

您无需创建管理员用户即可安装应用程序，如以下示例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

如果安装成功，则会显示以下消息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安装后，您可以使用 `admin:user:create` 命令：
[创建或编辑管理员](admin.md#create-or-edit-an-administrator)

#### 示例3 — 安装时带有其他选项

以下示例安装具有以下选项的应用程序：

* Magapplication安装在 `magento2` 与web服务器docroot相关的目录 `localhost` 而管理员的路径是 `admin`;因此：

   您的店面URL是 `http://127.0.0.1`

* 数据库服务器与Web服务器位于同一主机上。

   数据库名称为 `magento`，且用户名和密码均为 `magento`

* 管理员具有以下属性：

   * 名字和姓氏为 `Commerce User`
   * 用户名为 `admin` 密码是 `admin123`
   * 电子邮件地址为 `user@example.com`

* 默认语言为 `en_US` （美国英语）
* 默认货币为美元
* 默认时区为“美国中部”（美国/芝加哥）
* 安装程序先清理数据库，然后再安装表和模式
* 您使用 `ORD$` 销售订单增量前缀(因为它包含特殊字符 [`$`]，则值必须用双引号括起来)
* 会话数据保存在数据库中
* 使用服务器重写
* Elasticsearch7安装在 `es-host.example.com` 并连接端口9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>必须在一行上输入命令，或如上例所示，在 `\` 字符。

如果安装成功，则会显示以下消息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>如果您有一个用户帐户来访问应用程序服务器，请参阅 [设置umask](../next-steps/set-umask.md). 此类设置是共享托管的典型设置。
