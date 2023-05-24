---
title: 系统要求
description: 使用本参考可识别已在Adobe Commerce和Magento Open Source版本中测试的必需软件依赖项。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# 系统要求

此表显示了Adobe使用特定Adobe Commerce和Magento Open Source版本测试的第三方软件依赖项的版本。 Adobe仅支持下表中描述的系统要求组合。

例如，2.4.5已通过MariaDB 10.4进行全面测试。Adobe建议您在升级到2.4.5之前升级到MariaDB 10.4。

{{$include /help/_includes/templated/system-requirements-table.md}}

## 其他

本节介绍所有其他类型的必需软件和可选软件的支持和兼容性。

>[!NOTE]
>
>以下要求适用于Adobe Commerce和Magento Open Source的最新2.4.x补丁版本。

### 邮件服务器

邮件传输代理(MTA)或SMTP服务器

### 操作系统(Linux x86-64)

Linux发行版，如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。 不支持Microsoft Windows和macOS。

### PHP扩展

>[!NOTE]
>
>此 [PHP安装说明](prerequisites/php-settings.md) 包括安装这些扩展的步骤。

{{$include /help/_includes/templated/php-extensions.md}}

请参阅 [PHP官方文档](https://php.net/manual/en/extensions.php) 了解安装详细信息。

### PHP OPcache

我们强烈建议您确认 [PHP OPcache](https://php.net/manual/en/intro.opcache.php) 出于性能原因而启用。 OPcache在许多PHP分发中启用。 要验证是否已安装该软件，请参阅我们的 [PHP文档](prerequisites/php-settings.md).

如果您必须单独安装该软件，请参见 [PHP OPcache文档](https://php.net/manual/en/opcache.setup.php).

### PHP设置

我们建议使用特定的PHP配置设置，例如 `memory_limit`，可以避免使用Adobe Commerce和Magento Open Source时出现的常见问题。

有关更多信息，请参阅 [必需的PHP设置](prerequisites/php-settings.md).

### PHPUnit

PHPUnit（作为命令行工具）9.0.0

### RAM

升级从Commerce Marketplace和其他来源获得的应用程序和扩展最多可能需要2 GB的RAM。 如果您使用的系统RAM小于2 GB，建议您创建 [交换文件](https://support.magento.com/hc/en-us/articles/360032980432)；否则，升级可能会失败。

### 系统依赖关系

Adobe Commerce和Magento Open Source需要以下系统工具才能进行某些操作：

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- HTTPS需要有效的安全证书。
- 不支持自签名SSL证书。
- 传输层安全性(TLS)要求 — PayPal和 `repo.magento.com` 两者都需要TLS 1.2或更高版本。

### 支持的浏览器

店面和管理：

- Microsoft Edge（最新和以前的主要版本）
- Firefox（最新和以前的主要版本；任何操作系统）
- Chrome（最新和以前的主要版本；任何操作系统）
- Safari(最新和以前的主要版本；仅限macOS)
- 适用于iPad 2的Safari Mobile、iPad Mini、带有Retina Display的iPad(iOS 12或更高版本)、桌面店面
- 适用于iPhone 6或更高版本的Safari Mobile；适用于移动店面的iOS 12或更高版本
- Chrome for mobile (最新和以前的主要版本 [Android 4或更高版本] 适用于移动店面)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 或更高版本（仅限开发环境；可能对性能产生不利影响）

>[!NOTE]
>
>有一个已知问题 `xdebug` 会影响Adobe Commerce或Magento Open Source安装或安装后对店面或管理员的访问的其他限制条件。 有关详细信息，请参阅 [xdebug的已知问题](https://support.magento.com/hc/en-us/articles/360034242212).
