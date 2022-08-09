---
title: 设置引导参数的值
description: 了解如何为Commerce应用程序设置引导参数。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# Bootstrap参数

本主题演示了如何设置Commerce应用程序引导参数的值。 请参阅 [应用程序初始化和引导概述](initialization.md).

下表讨论了可设置的引导参数：

| Bootstrap参数 | 描述 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | 指定自定义目录和URL路径 |
| MAGE_PROFILER | 启用依赖关系图和HTML分析 |

>[!INFO]
>
>- 并非记录了所有引导参数。
>- 现在，您可以使用 [`magento deploy:mode:set {mode}`](../cli/set-mode.md) 命令。


## 使用环境变量设置参数

本节讨论如何使用环境变量设置引导参数的值。

### 设置应用程序模式

您可以将引导变量指定为系统范围的环境变量，以便所有进程都能使用它们。

例如，您可以使用 `MAGE_PROFILER` 系统环境变量以指定以下模式：

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

使用特定于shell的命令设置变量。 由于壳的语法不同，因此请参考 [unix.stackexchange.com][unix-stackx].

CentOS的Bash Shell示例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>如果 `PHP Fatal error` 在设置探查器值后，将在浏览器中显示，请重新启动web服务器。 原因可能与PHP字节码缓存有关，缓存字节码和PHP类路径。

## 设置Apache或Nginx的参数

本节讨论如何指定Apache或Nginx的模式。

### Nginx设置

请参阅 [Nginx示例配置] on _GitHub_.

### Apache .htaccess设置

设置应用程序模式的一种方法是通过编辑 `.htaccess`. 这样，您就不必更改Apache设置。

您可以修改 `.htaccess` ，具体取决于您指向Commerce应用程序的入口点：

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**设置变量**:

1. 在文本编辑器中打开任何上述文件，然后添加或取消对所需设置的注释。

   例如，要指定 [模式](application-modes.md)，取消以下注释：

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 设置的值 `MAGE_PROFILER` 以下任何一项：

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 将更改保存到 `.htaccess`;您无需重新启动Apache，所做的更改即可生效。

### Apache设置

Apache Web服务器支持使用 `mod_env` 指令。

《阿帕奇》 `mod_env` 指令在 [Apache版本2.2] 和 [Apache版本2.4].

以下步骤说明如何在Apache虚拟主机中设置应用程序模式。 这并非使用 `mod_env` 指令；有关详细信息，请参阅Apache文档。

>[!TIP]
>
>以下部分假定您已经设置了虚拟主机。 如果没有，请咨询资源，例如 [本DigitalOcean教程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**在Ubuntu上为Apache指定引导变量**:

1. 作为用户， `root` 权限，请在文本编辑器中打开虚拟主机配置文件。

   例如，如果虚拟主机名为 `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. 在虚拟主机配置中的任意位置，添加以下行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 保存更改并退出文本编辑器。
1. 如果尚未启用虚拟主机，请启用该虚拟主机：

   ```bash
   a2ensite <virtual host config file name>
   ```

   例如，

   ```bash
   a2ensite my.magento.conf
   ```

1. 设置模式后，重新启动Web服务器：

   - 乌本图： `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>本节假定您已经设置了虚拟主机。 如果没有，请咨询资源，例如 [本DigitalOcean教程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**在CentOS中为Apache指定引导变量**:

1. 作为用户， `root` 权限，打开 `/etc/httpd/conf/httpd.conf` 在文本编辑器中。

1. 在虚拟主机配置中的任意位置，添加以下行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 保存更改并退出文本编辑器。

1. 设置模式后，重新启动Web服务器：

   - 乌本图： `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache版本2.2]: http://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache版本2.4]: http://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx示例配置]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
