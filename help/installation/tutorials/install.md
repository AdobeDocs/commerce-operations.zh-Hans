---
title: 安装Adobe Commerce
description: 按照以下步骤在您拥有的基础架构上安装Adobe Commerce。
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '2094'
ht-degree: 0%

---

# 安装Adobe Commerce

在开始之前，请完成以下步骤：

* 验证您的系统是否满足中讨论的要求 [系统要求](../system-requirements.md).

* 全部完成 [先决条件](../prerequisites/overview.md) 任务。

* 完成第一个安装步骤。 请参阅 [安装或升级路径](../overview.md).

* 登录到应用程序服务器后， [切换到文件系统所有者](../prerequisites/file-system/overview.md).

* 查看 [命令行安装入门](../composer.md) 概述。

>[!NOTE]
>
>您必须从其安装应用程序 `bin` 子目录。

您可以使用不同的选项多次运行安装程序以完成如下安装任务：

* 分阶段安装 — 例如，在为Web服务器配置安全套接字层(SSL)后，可以再次运行安装程序以设置SSL选项。

* 更正以前安装中的错误。

* 在其他数据库实例中安装应用程序。

>[!NOTE]
>
>默认情况下，如果在同一数据库实例中安装Commerce软件，则安装程序不会覆盖该数据库。 您可以使用可选的 `cleanup-database` 用于更改此行为的参数。

另请参阅 [更新、重新安装、卸载](uninstall.md).

## 安全安装

{{$include /help/_includes/secure-install.md}}

## 安装程序帮助命令

可以运行以下命令来查找某些所需参数的值：

| 安装程序参数 | 命令 |
| ------------------ | ------------------------------- |
| 语言 | `magento info:language:list` |
| 货币 | `magento info:currency:list` |
| 时区 | `magento info:timezone:list` |

>[!NOTE]
>
>如果运行这些命令时显示错误，请验证是否已按照中所述更新了安装依赖关系 [更新安装依赖关系](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 从命令行安装

install命令使用以下格式：

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

下表描述了安装选项名称和值，如安装命令。 请参阅 [localhost安装示例](#sample-localhost-installations).

>[!NOTE]
>
>任何包含空格或特殊字符的选项都必须用单引号或双引号括起来。

**管理员凭据：**

以下选项指定管理员用户的用户信息和凭据。

在Adobe Commerce版本2.2.8及更高版本中，您可以在安装期间或安装之后创建管理员用户。 如果在安装期间创建用户，则需要所有管理员凭据变量。 请参阅 [localhost安装示例](#sample-localhost-installations).

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
| `--base-url` | 用于通过以下任意格式访问管理员和店面的基本URL：<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** 方案(http://或https://)和尾随斜杠都是必需的。<br><br>`<your install dir>` 是用来安装应用程序的docroot相对路径。 根据您设置Web服务器和虚拟主机的方式，路径可能是magento2或为空。<br><br>要访问本地主机上的应用程序，您可以使用 `http://127.0.0.1/<your install dir>/` 或 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 它表示由虚拟主机设置或Docker等虚拟化环境定义的基本URL。 例如，如果您使用主机名commerce.example.com设置虚拟主机，则可以安装应用程序 `--base-url={{base_url}}` 并使用如下的URL访问管理员 `http://commerce.example.com/admin`. | 是 |
| `--backend-frontname` | 用于访问管理员的统一资源标识符(URI)。 您可以忽略此参数，以便应用程序使用以下模式为您生成随机URI <code>admin_jkhgdfq</code>.<br><br>出于安全原因，我们建议使用随机URI。 黑客或恶意软件更难利用随机URI。<br><br>URI将显示在安装结束时。 您可以稍后随时使用 `magento info:adminuri` 命令。<br><br>如果您选择输入值，我们建议您不要使用诸如“管理员”、“后端”之类的常用词。 管理员URI可以包含字母数字值和下划线字符(`_`)。 | 否 |
| `--db-host` | 使用以下任一项：<br><br> — 数据库服务器的完全限定的主机名或IP地址。<br><br>- `localhost` （默认）或 `127.0.0.1` 如果数据库服务器与Web服务器位于同一主机上。localhost表示MySQL客户端库使用UNIX套接字连接到数据库。 `127.0.0.1` 导致客户端库使用TCP协议。 有关套接字的详细信息，请参见 [PHP PDO_MYSQL文档](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** 您可以选择在其主机名中指定数据库服务器端口，如www.example.com:9000 | 是 |
| `--db-name` | 要在其中安装数据库表的数据库实例的名称。<br><br>默认为 `magento2`. | 是 |
| `--db-user` | 数据库实例所有者的用户名。<br><br>默认为 `root`. | 是 |
| `--db-password` | 数据库实例所有者的密码。 | 是 |
| `--db-prefix` | 仅当在已有Adobe Commerce表的数据库实例中安装数据库表时才使用。<br><br>在这种情况下，请使用前缀来标识此安装的表。 有些客户在一台服务器上运行多个Adobe Commerce实例，该服务器上所有表都位于同一数据库中。<br><br>前缀最长可为5个字符。 它必须以字母开头，并且只能包含字母、数字和下划线字符。<br><br>此选项使这些客户能够在多个安装中共享数据库服务器。 | 否 |
| `--db-ssl-key` | 客户端密钥的路径。 | 否 |
| `--db-ssl-cert` | 客户端证书的路径。 | 否 |
| `--db-ssl-ca` | 服务器证书的路径。 | 否 |
| `--language` | 在管理员和店面中使用的语言代码。 (如果尚未这样做，可以通过输入以下内容查看语言代码列表 `magento info:language:list` 从bin目录中。) | 否 |
| `--currency` | 店面中使用的默认货币。 (如果尚未这样做，您可以通过输入货币来查看货币列表 `magento info:currency:list` 从bin目录中。) | 否 |
| `--timezone` | 在管理员和店面中使用的默认时区。 (如果尚未这样做，可以通过输入以下命令查看时区列表： `magento info:timezone:list` 从bin目录中。) | 否 |
| `--use-rewrites` | `1` 意味着您对店面和管理中生成的链接使用Web服务器重写。<br><br>`0` 禁用使用web服务器重写。 这是默认设置。 | 否 |
| `--use-secure` | `1` 允许在店面URL中使用安全套接字层(SSL)。 在选择此选项之前，请确保您的Web服务器支持SSL。<br><br>`0` 禁用使用SSL。 在这种情况下，所有其他安全URL选项也假定为0。 这是默认设置。 | 否 |
| `--base-url-secure` | 用于访问管理员和店面的安全基本URL，格式如下： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 是指使用SSL访问管理员。 在选择此选项之前，请确保您的Web服务器支持SSL。<br><br>`0` 表示您不将SSL与管理员一起使用。 这是默认设置。 | 否 |
| `--admin-use-security-key` | 1导致应用程序使用随机生成的键值来访问管理员和表单中的页面。 这些键值有助于防止跨站点脚本伪造攻击。 这是默认设置。<br><br>`0` 禁用键的使用。 | 否 |
| `--session-save` | 使用以下任一项：<br><br>- `db` 将会话数据存储到数据库中。 如果您有群集数据库，请选择数据库存储；否则，与基于文件的存储相比，这样做可能没有多大好处。<br><br>- `files` 将会话数据存储到文件系统中。 基于文件的会话存储是合适的，除非文件系统访问速度较慢，或者您拥有集群数据库，或者希望将会话数据存储在Redis中。<br><br>- `redis` 将会话数据存储在Redis中。 如果将Redis用于默认缓存或页面缓存，则必须已安装Redis。 有关配置对Redis的支持的其他信息，请参阅将Redis用于会话存储。 | 否 |
| `--key` | 如果您有密钥，请指定密钥以加密数据库中的敏感数据。 如果您没有，应用程序将为您生成一个。 | 是 |
| `--cleanup-database` | 若要在安装应用程序之前删除数据库表，请指定此参数，而不指定值。 否则，数据库将保持不变。 | 否 |
| `--db-init-statements` | 高级MySQL配置参数。 在连接到MySQL数据库时使用数据库初始化语句运行。 在设置任何值之前，请查阅与此类似的引用。<br><br>默认为 `SET NAMES utf8;`. | 否 |
| `--sales-order-increment-prefix` | 指定要用作销售订单前缀的字符串值。 通常，这用于保证支付处理者的唯一订单编号。 | 否 |

>[!TIP]
>
>要在安装期间启用远程存储服务，请参见 [配置远程存储](../../configuration/remote-storage/remote-storage.md) 在 _配置指南_.

**搜索引擎配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--search-engine` | 搜索引擎的版本。 可能的值包括 `elasticsearch7`， `elasticsearch6`、和 `elasticsearch5`. 默认为 `elasticsearch7`. 如果已安装OpenSearch作为搜索引擎，请指定值 `elasticsearch7`. Elasticsearch5已被弃用，不建议使用。 | 否 |
| `--elasticsearch-host` | 运行搜索引擎的主机名或IP地址。 默认为 `localhost`. | 否 |
| `--elasticsearch-port` | 传入HTTP请求的端口。 默认为 `9200`. | 否 |
| `--elasticsearch-index-prefix` | 标识搜索索引的前缀。 默认为 `magento2`. | 否 |
| `--elasticsearch-timeout` | 系统超时前的秒数。 默认为 `15`. | 否 |
| `--elasticsearch-enable-auth` | 在搜索引擎服务器上启用身份验证。 默认为 `false`. | 否 |
| `--elasticsearch-username` | 用于进行身份验证的用户ID | 否，除非启用身份验证 |
| `--elasticsearch-password` | 用于验证的密码 | 否，除非启用身份验证 |

**[!DNL RabbitMQ]配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--amqp-host` | 请勿使用 `--amqp` 选项，除非您已经设置了 [!DNL RabbitMQ]. 请参阅 [!DNL RabbitMQ] 安装，以了解有关安装和配置的更多信息 [!DNL RabbitMQ].<br><br>主机名，其中 [!DNL RabbitMQ] 已安装。 | 否 |
| `--amqp-port` | 用于连接的端口 [!DNL RabbitMQ]. 默认值为5672。 | 否 |
| `--amqp-user` | 用于连接到的用户名 [!DNL RabbitMQ]. 不使用默认用户 `guest`. | 否 |
| `--amqp-password` | 用于连接的密码 [!DNL RabbitMQ]. 不使用默认密码 `guest`. | 否 |
| `--amqp-virtualhost` | 用于连接的虚拟主机 [!DNL RabbitMQ]. 默认为 `/`. | 否 |
| `--amqp-ssl` | 指示是否连接到 [!DNL RabbitMQ]. 默认为 `false`. 请参阅 [!DNL RabbitMQ] 有关为设置SSL的信息 [!DNL RabbitMQ]. | 否 |
| `--consumers-wait-for-messages` | 消费者是否应该等待队列中的消息？ 1 — 是，0 — 否 | 否 |

**远程存储选项：**

| 名称 | 描述 | 必需？ |
|--- |--- |--- |
| `remote-storage-driver` | 适配器名称<br>可能的值：<br>**文件**：禁用远程存储并使用本地文件系统&#x200B;<br>**aws-s3**：使用 [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) | 否 |
| `remote-storage-bucket` | 对象存储或容器名称 | 否 |
| `remote-storage-prefix` | 可选前缀（对象存储内的位置） | 否 |
| `remote-storage-region` | 区域名称 | 否 |
| `remote-storage-key` | 可选访问密钥 | 否 |
| `remote-storage-secret` | 可选密钥 | 否 |

**锁定配置选项：**

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--lock-provider` | 锁定提供程序名称。<br><br>可用的锁定提供程序： `db`， `zookeeper`， `file`.<br><br>默认锁定提供程序： `db` | 否 |
| `--lock-db-prefix` | 使用时避免锁定冲突的特定数据库前缀 `db` 锁定提供程序。<br><br>默认值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用时连接到Zookeeper群集的主机和端口 `zookeeper` 锁定提供程序。<br><br>例如： `127.0.0.1:2181` | 是，如果您设置 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存锁的路径。<br><br>默认路径为： `/magento/locks` | 否 |
| `--lock-file-path` | 保存文件锁定的路径。 | 是，如果您设置 `--lock-provider=file` |

**使用者配置选项：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>要在安装应用程序后启用或禁用模块，请参阅 [启用和禁用模块](manage-modules.md).

**敏感数据：**

{{$include /help/_includes/sensitive-data.md}}

### localhost安装示例

以下示例显示了使用各种选项在本地安装Adobe Commerce的命令。

#### 示例1 — 使用管理员用户帐户进行基本安装

以下示例使用下列选项安装应用程序：

* 应用程序安装在 `magento2` 相对于Web服务器docroot开启的目录 `localhost` 管理员的路径为 `admin`；因此：

  您的店面URL为 `http://127.0.0.1`

* 数据库服务器与Web服务器位于同一主机上。

  数据库名称为 `magento`，用户名和密码均为 `magento`

* 使用服务器重写

* 管理员具有以下属性：

   * 名字和姓氏是 `Commerce User`
   * 用户名是 `admin` 密码是 `admin123`
   * 电子邮件地址为 `user@example.com`

* 默认语言为 `en_US` （美国英语）
* 默认货币为美元
* 默认时区为美国中部（美洲/芝加哥）
* Elasticsearch7安装在 `es-host.example.com` 并连接到端口9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

类似于以下内容的消息显示指示安装成功：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 示例2 — 没有管理员用户帐户的基本安装

您可以安装应用程序而不创建管理员用户，如以下示例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

如果安装成功，将显示如下消息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安装后，您可以使用 `admin:user:create` 命令：
[创建或编辑管理员](admin.md#create-or-edit-an-administrator)

#### 示例3 — 使用其他选项进行安装

以下示例使用下列选项安装应用程序：

* Magapplication安装在 `magento2` 相对于Web服务器docroot开启的目录 `localhost` 管理员的路径为 `admin`；因此：

  您的店面URL为 `http://127.0.0.1`

* 数据库服务器与Web服务器位于同一主机上。

  数据库名称为 `magento`，用户名和密码均为 `magento`

* 管理员具有以下属性：

   * 名字和姓氏是 `Commerce User`
   * 用户名是 `admin` 密码是 `admin123`
   * 电子邮件地址为 `user@example.com`

* 默认语言为 `en_US` （美国英语）
* 默认货币为美元
* 默认时区为美国中部（美洲/芝加哥）
* 安装程序先清理数据库，然后再安装表和模式
* 您使用 `ORD$` 销售订单增量前缀（因为它包含特殊字符） [`$`]，该值必须用双引号括起来)
* 会话数据保存在数据库中
* 使用服务器重写
* Elasticsearch7安装在 `es-host.example.com` 并连接到端口9200

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
>必须在一行中输入命令，或者如上例所示，使用 `\` 每行结尾的字符。

如果安装成功，将显示如下消息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>如果您有一个用于访问应用程序服务器的用户帐户，请参阅 [设置umask](../next-steps/set-umask.md). 此类设置是共享托管的典型设置。
