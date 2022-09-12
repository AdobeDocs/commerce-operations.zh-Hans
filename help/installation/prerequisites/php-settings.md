---
title: PHP设置
description: 请按照以下步骤来安装所需的PHP扩展，并为Adobe Commerce和Magento Open Source的本地安装配置所需的PHP设置。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# PHP设置

本主题讨论如何设置必需项 [PHP](https://glossary.magento.com/php) 选项。

>[!NOTE]
>
>请参阅 [系统要求](../system-requirements.md) ，以了解支持的PHP版本。

## 验证PHP是否已安装

大多数版本的Linux默认安装PHP。 本主题假定您已安装PHP。 要验证PHP是否已安装，请在命令行中键入：

```bash
php -v
```

如果 [PHP](https://glossary.magento.com/php) ，将显示一条与以下内容类似的消息：

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce和Magento Open Source2.4与PHP 7.3兼容，但我们使用PHP 7.4进行测试，并建议使用。

如果未安装PHP，或需要升级版本，请按照特定Linux版本的说明进行安装。
在CentOS上， [可能需要其他步骤](https://wiki.centos.org/HowTos/php7).

## 验证已安装的扩展

Adobe Commerce和Magento Open Source需要安装一组扩展。

{{$include /help/_includes/php-extensions.md}}

要验证已安装的扩展，请执行以下操作：

1. 列出已安装的模块。

   ```bash
   php -m
   ```

1. 验证是否已安装所有必需的扩展。
1. 使用与安装PHP相同的工作流添加任何缺失的模块。 例如，如果您使用 `yum` 要安装PHP，可添加PHP 7.4模块，具有：

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## 检查PHP设置

>[!WARNING]
>
>如果您使用的是PHP 7.4.20，请设置 `pcre.jit=0` 在 `php.ini` 文件。 这是一个PHP [错误](https://bugs.php.net/bug.php?id=81101) 来阻止加载CSS。

- 为PHP设置系统时区；否则，在安装期间显示以下错误以及cron等与时间相关的操作可能无法正常工作：

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- 设置PHP内存限制。

   我们的详细建议包括：

   - 编译代码或部署静态资产， `1G`
   - 调试、 `2G`
   - 测试， `~3-4G`

- 增加PHP的值 `realpath_cache_size` 和 `realpath_cache_ttl` 在推荐的设置中：

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   这些设置允许PHP进程缓存指向文件的路径，而不是每次加载页面时都查找它们。 请参阅 [性能优化](https://www.php.net/manual/en/ini.core.php) （在PHP文档中）。

- 启用 [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)，这是Adobe Commerce和Magento Open Source2.1及更高版本的必需函数。

   我们建议您启用 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) 出于性能原因。 在许多PHP分发中已启用OPcache。

   Adobe Commerce和Magento Open Source2.1及更高版本使用PHP代码注释生成代码。

>[!NOTE]
>
>为避免在安装和升级过程中出现问题，我们强烈建议您将相同的PHP设置应用于PHP命令行配置和PHP Web服务器插件配置。 有关更多信息，请参阅下一节。

## 查找PHP配置文件

本节将讨论如何查找更新所需设置所需的配置文件。

### 查找 `php.ini` 配置文件

要查找Web服务器配置，请运行 [`phpinfo.php` 文件](optional-software.md#create-phpinfophp) 并查找 `Loaded Configuration File` 如下所示：

![PHP信息页](../../assets/installation/config_phpini-webserver.png)

要找到PHP命令行配置，请输入

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>如果您只有一个 `php.ini` 文件中进行更改。 如果你有两个 `php.ini` 文件，请在 *全部* 文件。 如果不这样做，可能会导致无法预知的性能。

### 查找OPcache配置设置

PHP OPcache设置通常位于 `php.ini` 或 `opcache.ini`. 位置可能取决于您的操作系统和PHP版本。 OPcache配置文件可能具有 `opcache` 或 `opcache.enable`.

请遵循以下准则来查找：

- Apache Web服务器：

   对于具有Apache的Ubuntu，OPcache设置通常位于 `php.ini` 文件。

   对于具有Apache或nginx的CentOS，OPcache设置通常位于 `/etc/php.d/opcache.ini`

   如果没有，请使用以下命令找到它：

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- 带有PHP-FPM的nginx Web服务器： `/etc/php/7.2/fpm/php.ini`

如果您有多个 `opcache.ini`，请修改所有这些变量。

## 如何设置PHP选项

要设置PHP选项，请执行以下操作：

1. 打开 `php.ini` 在文本编辑器中。
1. 在 [时区设置](https://www.php.net/manual/en/timezones.php)
1. 找到以下设置，并在必要时取消注释：

   ```conf
   date.timezone =
   ```

1. 添加您在步骤2中找到的时区设置。

1. 更改 `memory_limit` 到此部分开头建议的值之一。

   例如，

   ```conf
   memory_limit=2G
   ```

1. 添加或更新 `realpath_cache` 配置以匹配以下值：

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. 保存更改并退出文本编辑器。

1. 打开另一个 `php.ini` （如果它们不同），并在其中进行相同的更改。

## 设置OPcache选项

要设置 `opcache.ini` 选项：

1. 在文本编辑器中打开OPcache配置文件：

   - `opcache.ini` (CentOS)
   - `php.ini` （乌本图）
   - `/etc/php/7.2/fpm/php.ini` (nginx Web服务器（CentOS或Ubuntu）)

1. 定位 `opcache.save_comments` 并在必要时取消注释。
1. 确保将其值设置为 `1`.
1. 保存更改并退出文本编辑器。
1. 重新启动Web服务器：

   - 阿帕奇、乌本图： `service apache2 restart`
   - Apache、CentOS: `service httpd restart`
   - nginx、Ubuntu和CentOS: `service nginx restart`

## 疑难解答

请参阅以下Adobe Commerce支持文章，以获取PHP问题疑难解答帮助：

- [在浏览器中访问Adobe Commerce时出现PHP版本错误或404错误](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP设置错误](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [未正确安装PHP mcrypt扩展](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP版本准备情况检查问题](https://support.magento.com/hc/en-us/articles/360033546411)
- [常见PHP致命错误及解决方案](https://support.magento.com/hc/en-us/articles/360030568432)
