---
title: 配置存储
description: 按照以下步骤配置您的Adobe Commerce或Magento Open Source商店。
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# 配置存储

运行此命令之前，必须执行以下操作 *或* 您必须 [安装应用程序](../advanced.md)：

* [创建或更新部署配置](deployment.md)
* [创建数据库模式](database.md)

## 安全安装

{{$include /help/_includes/secure-install.md}}

## 配置存储

命令用法：

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

其中下表定义了参数和值：

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--base-url` | 用于通过以下任意格式访问管理员和店面的基本URL：<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** 方案(`http://` 或 `https://`)和尾随斜杠都是必需的。 `<your install dir>` 是用来安装应用程序的docroot相对路径。 根据您设置Web服务器和虚拟主机的方式，路径可能是magento2或为空。<br><br>要访问本地主机上的应用程序，您可以使用 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 它表示由虚拟主机设置或Docker等虚拟化环境定义的基本URL。 例如，如果您使用主机名commerce.example.com设置虚拟主机，则可以安装应用程序 `--base-url={{base_url}}` 并使用如下的URL访问管理员 `http://commerce.example.com/admin`. | 否 |
| `--language` | 在管理员和店面中使用的语言代码。<br><br>(如果尚未这样做，可以通过输入以下内容查看语言代码列表 `magento info:language:list` 从 `bin` 目录。) | 否 |
| `--currency` | 店面中使用的默认货币。 <br><br>(如果尚未这样做，您可以通过输入货币来查看货币列表 `magento info:currency:list` 从 `bin` 目录。) | 否 |
| `--timezone` | 在管理员和店面中使用的默认时区。 (如果尚未这样做，可以通过输入以下命令查看时区列表： `magento info:timezone:list` 从 `bin` 目录。) | 否 |
| `--use-rewrites` | `1` 意味着您对店面和管理中生成的链接使用Web服务器重写。<br><br>`0` 禁用使用web服务器重写。 这是默认设置。 | 否 |
| `--use-secure` | `1` 允许在店面URL中使用安全套接字层(SSL)。 在选择此选项之前，请确保您的Web服务器支持SSL。<br><br>`0` 禁用使用SSL。 在这种情况下，所有其他安全URL选项也假定为0。 这是默认设置。 | 否 |
| `--base-url-secure` | 用于访问管理员和店面的安全基本URL，格式如下： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 是指使用SSL访问管理员。 在选择此选项之前，请确保您的Web服务器支持SSL。<br><br>`0` 表示您不将SSL与管理员一起使用。 这是默认设置。 | 否 |
| `--admin-use-security-key` | `1` 使应用程序使用随机生成的键值来访问管理员和表单中的页面。 这些键值有助于防止跨站点脚本伪造攻击。 这是默认设置。<br/><br/>`0` 禁用键的使用。 | 否 |
| `--magento-init-params` | 添加到任何命令以自定义应用程序初始化参数<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |
