---
title: 系统要求
description: 使用本参考可确定已通过Adobe Commerce和Magento Open Source版本测试的所需软件依赖项。
source-git-commit: 3ba17b62f595e5a02ca56753d81d67166ddbc413
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# 系统要求

此表显示了Adobe已通过特定Adobe Commerce和Magento Open Source版本测试的第三方软件依赖项的版本。 Adobe仅支持下表所述的系统要求组合。

例如，2.4.3已通过MariaDB 10.4的完全测试。Adobe建议您在升级到2.4.3之前升级到MariaDB 10.4。

{{$include /help/_includes/templated/system-requirements-table.md}}

## 其他

本节介绍所有其他类型必需和可选软件的支持和兼容性。

>[!NOTE]
>
>以下要求适用于Adobe Commerce和Magento Open Source的最新2.4.x修补程序版本。

### 邮件服务器

邮件传输代理(MTA)或SMTP服务器

### 操作系统(Linux x86-64)

Linux发行版，如RedHat Enterprise Linux(RHEL)、CentOS、Ubuntu、Debian等。 Microsoft Windows和macOS不受支持。

### PHP扩展

>[!NOTE]
>
>的 [PHP安装说明](prerequisites/php-settings.md) 包括安装这些扩展的步骤。

{{$include /help/_includes/php-extensions.md}}

请参阅 [官方PHP文档](https://php.net/manual/en/extensions.php) 以了解安装详细信息。

### PHP OPcache

我们强烈建议您验证 [PHP OPcache](https://php.net/manual/en/intro.opcache.php) 因性能原因而启用。 在许多PHP分发中已启用OPcache。 要验证是否已安装，请参阅 [PHP文档](prerequisites/php-settings.md).

如果必须单独安装，请参阅 [PHP OPcache文档](https://php.net/manual/en/opcache.setup.php).

### PHP设置

我们建议使用特定的PHP配置设置，例如 `memory_limit`，可避免在使用Adobe Commerce和Magento Open Source时出现常见问题。

有关更多信息，请参阅 [所需的PHP设置](prerequisites/php-settings.md).

### PHPUnit

PHPUnit（作为命令行工具）9.0.0

### RAM

升级您从Commerce Marketplace和其他源获取的应用程序和扩展可能需要多达2 GB的RAM。 如果您使用的系统内存小于2 GB，我们建议您创建 [交换文件](https://support.magento.com/hc/en-us/articles/360032980432);否则，升级可能会失败。

### 系统依赖关系

Adobe Commerce和Magento Open Source需要以下系统工具才能执行某些操作：

- [bash](https://www.gnu.org/software/bash/)
- [gzip](https://www.gzip.org/)
- [lsof](https://linux.die.net/man/8/lsof)
- [mysql](https://www.mysql.com/)
- [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [好](https://linux.die.net/man/1/nice)
- [php](https://www.php.net/)
- [sed](https://www.gnu.org/software/sed/manual/sed.html)
- [焦油](https://linux.die.net/man/1/tar)

### SSL

- 有效 [安全证书](https://glossary.magento.com/security-certificate) 是HTTPS所必需的。
- 不支持自签名SSL证书。
- 传输层安全性(TLS)要求 — PayPal和 `repo.magento.com` 都需要TLS 1.2或更高版本。

### 支持的浏览器

店面和管理员：

- Microsoft Edge（最新和以前的主要版本）
- Firefox(最新和以前的主要版本；任何操作系统)
- Chrome(最新及以前的主要版本；任何操作系统)
- Safari(最新和以前的主要版本；仅macOS)
- 适用于iPad 2、iPad Mini、iPad的Safari Mobile（带Retina显示屏）(iOS 12或更高版本)，适用于桌面店面
- 适用于iPhone 6或更高版本的Safari Mobile;iOS 12或更高版本，用于移动店面
- 适用于移动设备的Chrome（最新和以前的主要版本） [Android 4或更高版本] （适用于移动店面）

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 或更高版本（仅限开发环境）；会对绩效产生不利影响)

>[!NOTE]
>
>存在一个已知的问题 `xdebug` 会影响Adobe Commerce或Magento Open Source安装，或在安装后访问storefront或Admin的权限。 有关详细信息，请参阅 [xdebug的已知问题](https://support.magento.com/hc/en-us/articles/360034242212).
