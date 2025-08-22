---
title: PHP设置
description: 按照以下步骤安装所需的PHP扩展，并为Adobe Commerce的内部安装配置所需的PHP设置。
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# PHP设置

本主题讨论如何设置所需的PHP选项。

>[!NOTE]
>
>最新版本的Adobe Commerce至少需要8.1个PHP。有关所有支持的PHP版本，请参阅[系统要求](../system-requirements.md)。

有关云配置指南，请参阅[云基础架构上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html)指南中的&#x200B;_PHP设置_。

## PHP进程控制

{{php-process-control}}

## 验证是否已安装PHP

默认情况下，大多数Linux发行版中都安装了PHP。 本主题假定您已安装PHP。 要验证是否已安装PHP，请在命令行中输入以下内容：

```bash
php -v
```

如果安装了PHP，则会显示类似于以下内容的消息：

```
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

如果未安装PHP（或需要升级），请按照Linux分发的说明进行安装。

## 验证已安装的扩展

Adobe Commerce需要特定的PHP扩展。 以下列表指定了每个Commerce版本所需的扩展。 这些列表是从运行每个版本最新版本的部署自动生成的。

{{$include /help/_includes/templated/php-extensions.md}}

要验证已安装的扩展，请执行以下操作：

1. 列出已安装的模块。

   ```bash
   php -m
   ```

1. 验证是否已安装所有必需的扩展。
1. 使用用于安装PHP的相同工作流添加任何缺少的模块。

## 检查PHP设置

>[!WARNING]
>
>如果您使用的是PHP 7.4.20，请在`pcre.jit=0`文件中设置`php.ini`。 这会绕过PHP [错误](https://bugs.php.net/bug.php?id=81101)而阻止加载CSS。

- 为PHP设置系统时区；否则，安装期间显示的以下错误以及与时间相关的操作（如cron ）可能无法工作：

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- 设置PHP内存限制

  Adobe建议执行以下操作：

   - 正在编译代码或部署静态资源，`1G`
   - 调试，`2G`
   - 正在测试，`~3-4G`

- 将PHP `realpath_cache_size`和`realpath_cache_ttl`的值增加到建议的设置：

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  这些设置允许PHP进程将路径缓存到文件，而不是在页面加载时查找文件。 请参阅PHP文档中的[性能调整](https://www.php.net/manual/en/ini.core.php)。

- 启用Adobe Commerce 2.1及更高版本所需的[`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)。

  出于性能原因，Adobe建议启用[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)。 OPcache在许多PHP分发中启用。

  Adobe Commerce 2.1及更高版本使用PHP代码注释来生成代码。

>[!NOTE]
>
>为避免在安装和升级过程中出现问题，Adobe强烈建议将相同的PHP设置同时应用于PHP命令行配置和PHP Web服务器插件配置。 有关更多信息，请参阅下一部分。

## 查找PHP配置文件

本节讨论如何查找更新所需设置所需的配置文件。

### 查找`php.ini`配置文件

要查找Web服务器配置，请在Web浏览器中运行[`phpinfo.php`文件](optional-software.md#create-phpinfophp)并查找`Loaded Configuration File`，如下所示：

![PHP信息页](../../assets/installation/config_phpini-webserver.png)

要定位PHP命令行配置，请输入

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>如果您只有一个`php.ini`文件，请更改该文件。 如果您有两个`php.ini`文件，请更改&#x200B;*两个*&#x200B;文件。 否则，可能会导致性能不可预测。

### 查找OPcache配置设置

PHP OPcache设置通常位于`php.ini`或`opcache.ini`中。 该位置可能取决于您的操作系统和PHP版本。 OPcache配置文件可能具有`opcache`部分或类似于`opcache.enable`的设置。

请使用以下指南查找它：

- Apache Web Server：

  对于带有Apache的Ubuntu，OPcache设置通常位于`php.ini`文件中。

  对于具有Apache或nginx的CentOS，OPcache设置通常位于`/etc/php.d/opcache.ini`中

  如果没有，请使用以下命令找到它：

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- 带有PHP-FPM的nginx Web服务器： `/etc/php/8.1/fpm/php.ini`

如果您有多个`opcache.ini`，请修改全部。

## 如何设置PHP选项

要设置PHP选项：

1. 在文本编辑器中打开`php.ini`。
1. 在可用的[时区设置](https://www.php.net/manual/en/timezones.php)中找到服务器的时区
1. 找到以下设置并在必要时取消注释：

   ```conf
   date.timezone =
   ```

1. 添加您在步骤2中找到的时区设置。

1. 将`memory_limit`的值更改为本节开头建议的值之一。

   例如，

   ```conf
   memory_limit=2G
   ```

1. 添加或更新`realpath_cache`配置以匹配以下值：

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

1. 打开其他`php.ini`（如果它们不同）并在其中进行相同的更改。

## 设置OPcache选项

要设置`opcache.ini`选项：

1. 在文本编辑器中打开OPcache配置文件：

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (nginx Web服务器（CentOS或Ubuntu）)

1. 找到`opcache.save_comments`并在必要时取消其注释。
1. 确保其值设置为`1`。
1. 保存更改并退出文本编辑器。
1. 重新启动Web服务器：

   - Apache， Ubuntu： `service apache2 restart`
   - Apache， CentOS： `service httpd restart`
   - nginx、Ubuntu和CentOS： `service nginx restart`

## 故障排除

有关解决PHP问题的帮助，请参阅以下Adobe Commerce支持文章：

- 在浏览器中访问Adobe Commerce时，[PHP版本错误或404错误](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP设置错误](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- 未正确安装[PHP mcrypt扩展](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP版本准备情况检查问题](https://support.magento.com/hc/en-us/articles/360033546411)
- [常见PHP错误和解决方案](https://support.magento.com/hc/en-us/articles/360030568432)

<!-- Last updated from includes: 2025-04-04 22:27:22 -->
