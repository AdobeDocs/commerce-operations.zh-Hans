---
title: 创建或更新部署配置
description: 按照以下步骤管理Adobe Commerce部署配置。
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# 创建或更新部署配置

使用此命令没有先决条件。

## 创建或更新部署配置

[部署配置](../../configuration/reference/deployment-files.md)提供了应用程序需要初始化和引导的信息。

在以下情况下，可以使用此命令：

* 您之前安装了应用程序，并且想要修改部署配置
* 您希望仅创建部署配置，并以其他方式继续安装
* 更新部署配置而不影响其他任何内容

命令选项：

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

下表讨论了安装参数和值的含义。

| 参数 | 值 | 必需？ |
|--- |--- |--- |
| `--backend-frontname` | 用于访问管理员的统一资源标识符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。<br><br>为防止利用漏洞攻击，建议您不要使用“管理员”、“后端”等常用词。 管理员URI只能包含字母数字值和下划线字符(`_`)。 | 否 |
| `--db-host` | 使用以下任一项：<br><br> — 数据库服务器的完全限定主机名或IP地址。<br><br>- `localhost`（默认）或`127.0.0.1`（如果数据库服务器与Web服务器位于同一主机上）。 localhost表示MySQL客户端库使用UNIX套接字连接到数据库。 `127.0.0.1`导致客户端库使用TCP协议。 有关套接字的详细信息，请参阅[PHP PDO_MYSQL文档](https://www.php.net/manual/en/ref.pdo-mysql.php)。<br><br>**注意：**&#x200B;您可以选择在其主机名中指定数据库服务器端口，如`www.example.com:9000` | 否 |
| `--db-name` | 要在其中安装数据库表的数据库实例的名称。<br><br>默认值为`magento2`。 | 否 |
| `--db-user` | 数据库实例所有者的用户名。<br><br>默认值为`root`。 | 否 |
| `--db-password` | 数据库实例所有者的密码。 | 否 |
| `--db-prefix` | 仅当在已有Adobe Commerce表的数据库实例中安装数据库表时才使用。<br><br>在这种情况下，请使用前缀来标识此安装的表。 有些客户在一台服务器上运行多个Adobe Commerce实例，该服务器上所有表都位于同一数据库中。<br><br>前缀长度最多可为5个字符。 它必须以字母开头，并且只能包含字母、数字和下划线字符。<br><br>此选项使这些客户能够与多个Adobe Commerce安装共享数据库服务器。 | 否 |
| `--session-save` | 使用以下任一项： <br><br>- `db`将会话数据存储在[数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)中。 如果您有群集数据库，请选择数据库存储；否则，与基于文件的存储相比，这样做可能没有多大好处。<br><br>- `files`以在文件系统中存储会话数据。 基于文件的会话存储是合适的，除非文件系统访问速度较慢，或者您拥有集群数据库，或者希望将会话数据存储在Redis中。<br><br>- `redis`将会话数据存储在[使用Redis进行会话存储](../../configuration/cache/config-redis.md)。 如果将Redis用于默认缓存或页面缓存，则必须已安装Redis。 | 否 |
| `--key` | 如果您有密钥，请指定密钥以加密数据库中的[敏感数据](#sensitive-data)。 如果您没有，应用程序将为您生成一个。 | 否 |
| `--db-init-statements` | 高级MySQL配置参数。 在连接到MySQL数据库时使用数据库初始化语句运行。<br><br>默认值为`SET NAMES utf8;`。<br><br>在设置任何值之前，请查阅类似于[此引用](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)的引用。 | 否 |
| `--http-cache-hosts` | 要向其发送清除请求的HTTP缓存网关主机的逗号分隔列表。 （例如，Varnish服务器。） 使用此参数可指定要在同一请求中清除的一个或多个主机。 （无论您是只有一个主机还是多个主机。）<br><br>格式必须为`<hostname or ip>:<listen port>`，如果端口为80，则可以省略`<listen port>`。 例如，`--http-cache-hosts=192.0.2.100,192.0.2.155:6081`。 不要使用空格字符分隔主机。 | 否 |

## 导入配置数据

设置生产系统时，最好将配置设置从`config.php`和`env.php`导入数据库。
这些设置包括配置路径和值、网站、商店、商店视图和主题。

导入网站、商店、商店视图和主题后，您可以创建产品属性，并在生产系统上将其应用于网站、商店和商店视图。

在生产系统上，运行以下命令以将数据从配置文件（`config.php`和`env.php`）导入数据库：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

可选的`[-n, --no-interaction]`标志允许命令运行，而不需要其他确认。

有关其他信息，请检查[从配置文件导入数据](../../configuration/cli/import-configuration.md)

### 敏感数据

{{$include /help/_includes/sensitive-data.md}}
