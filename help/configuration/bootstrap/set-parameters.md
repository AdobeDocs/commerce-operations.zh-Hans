---
title: 设置引导参数值
description: 了解如何为Commerce应用程序设置引导参数。
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Bootstrap参数

本主题演示如何设置Commerce应用程序引导参数的值。 请参阅[应用程序初始化和引导概述](initialization.md)。

下表讨论了可以设置的引导参数：

| Bootstrap参数 | 描述 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | 指定自定义目录和URL路径 |
| MAGE_PROFILER | 启用依赖关系图和HTML分析 |

>[!INFO]
>
>- 并非所有引导数据库参数都得到了记录。
>- 您现在可以使用[`magento deploy:mode:set {mode}`](../cli/set-mode.md)命令设置应用程序模式（开发人员、默认、生产）。

## 使用环境变量设置参数

本节讨论如何使用环境变量设置引导参数的值。

### 设置应用程序模式

您可以将引导数据库变量指定为系统范围环境变量，这样所有进程都可以使用这些变量。

例如，您可以使用`MAGE_PROFILER`系统环境变量指定模式，如下所示：

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

使用特定于shell的命令设置变量。 由于外壳的语法不同，请查阅[unix.stackexchange.com][unix-stackx]之类的引用。

CentOS的Bash shell示例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>如果在设置探查器值后浏览器中显示`PHP Fatal error`，请重新启动Web服务器。 原因可能与PHP字节码缓存有关，该缓存会缓存字节码和PHP类路径。

## 设置Apache或Nginx的参数

本节讨论如何为Apache或Nginx指定模式。

### Nginx设置

查看&#x200B;_GitHub_&#x200B;上的[Nginx示例配置]。

### Apache .htaccess设置

设置应用程序模式的一种方法是编辑`.htaccess`。 这样，您就不必更改Apache设置。

您可以修改以下任意位置的`.htaccess`，具体取决于您进入Commerce应用程序的入口点：

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**设置变量**：

1. 在文本编辑器中打开任何上述文件，然后添加或取消注释所需的设置。

   例如，要指定[模式](application-modes.md)，请取消注释以下内容：

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 将`MAGE_PROFILER`的值设置为以下任意值：

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 将更改保存到`.htaccess`；无需重新启动Apache更改即可生效。

### Apache设置

Apache Web Server支持使用`mod_env`指令设置应用程序模式。

Apache `mod_env`指令在[Apache版本2.2]和[Apache版本2.4]中略有不同。

下面的过程说明了如何在Apache虚拟主机中设置应用程序模式。 这不是使用`mod_env`指令的唯一方法；有关详细信息，请参阅Apache文档。

>[!TIP]
>
>以下部分假设您已设置虚拟主机。 如果您还没有这样的文件，请查阅诸如[此DigitalOcean教程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)之类的资源。

**为Ubuntu上的Apache指定引导变量**：

1. 作为具有`root`权限的用户，在文本编辑器中打开您的虚拟主机配置文件。

   例如，如果您的虚拟主机名为`my.magento`，

   - Apache 2.4： `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2： `vim /etc/apache2/sites-available/my.magento`

1. 在虚拟主机配置中的任意位置，添加以下行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 保存更改并退出文本编辑器。
1. 启用虚拟主机（如果尚未启用）：

   ```bash
   a2ensite <virtual host config file name>
   ```

   例如，

   ```bash
   a2ensite my.magento.conf
   ```

1. 设置模式后，重新启动Web服务器：

   - Ubuntu： `service apache2 restart`
   - CentOS： `service httpd restart`

>[!TIP]
>
>本节假定您已设置虚拟主机。 如果您还没有这样的文件，请查阅诸如[此DigitalOcean教程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6)之类的资源。

**要为CentOS上的Apache指定引导变量**：

1. 作为具有`root`权限的用户，在文本编辑器中打开`/etc/httpd/conf/httpd.conf`。

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

   - Ubuntu： `service apache2 restart`
   - CentOS： `service httpd restart`

<!-- link definitions -->

[Apache版本2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache版本2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx示例配置]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
