---
title: 完整先决条件
description: 通过完成这些先决步骤，为升级准备Adobe Commerce或Magento Open Source项目。
source-git-commit: 0729e84adabcded6d50cf28a7525b97fd50d45f5
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 0%

---


# 完成升级先决条件

了解运行Adobe Commerce或Magento Open Source所需的内容非常重要。 您必须先查看 [系统要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 对于您计划升级到的版本。

在查看系统要求后，您必须先完成以下先决条件，然后才能升级系统：

- 更新所有软件
- 验证是否安装了支持的搜索引擎
- 设置打开的文件限制
- 验证cron作业是否正在运行
- 已设置 `DATA_CONVERTER_BATCH_SIZE`
- 验证文件系统权限
- 设置 `pub/` 目录根目录
- 安装编辑器更新插件

## 更新所有软件

的 [系统要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 准确描述哪些第三方软件版本已在Adobe Commerce和Magento Open Source版本中进行了测试。

确保更新了环境中的所有系统要求和依赖项。 请参阅PHP [7.4](https://www.php.net/manual/en/migration74.php)、PHP [8.0](https://www.php.net/manual/en/migration80.php)、PHP [8.1](https://www.php.net/manual/en/migration81.php)和 [所需的PHP设置](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html#php-required-set).

## 验证是否安装了支持的搜索引擎

Adobe Commerce和Magento Open Source需要安装Elasticsearch或OpenSearch才能使用软件。

**如果您从2.3.x升级到2.4**，则必须检查在2.3.x实例中是使用MySQL、Elasticsearch还是第三方扩展作为目录搜索引擎。 结果决定了您必须执行的操作 _之前_ 升级到2.4。

**如果您升级的是2.3.x或2.4.x发行版中的修补程序版本**，如果已安装Elasticsearch7.x，则可以选择 [迁移到OpenSearch](opensearch-migration.md).

您可以使用命令行或管理员来确定目录搜索引擎：

- 输入 `bin/magento config:show catalog/search/engine` 命令。 该命令返回值 `mysql`, `elasticsearch` (表示已配置Elasticsearch2), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`，或自定义值，表示您已安装第三方搜索引擎。 值 `elasticsearch7` 表示安装了Elasticsearch7或OpenSearch。

- 在管理员中，检查 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** 字段。

以下各节介绍在升级到2.4.0之前必须执行哪些操作。

### MySQL

自2.4起，MySQL不再是受支持的目录搜索引擎。 升级前，必须安装并配置Elasticsearch或OpenSearch。 使用以下资源帮助您完成此过程：

- [安装和配置Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-overview.html)
- [安装Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- 配置 [nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html) 或 [Apache](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html) 与搜索引擎结合使用
- [配置商务以使用Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 重新索引

某些第三方目录搜索引擎在Adobe Commerce搜索引擎上运行。 请联系您的供应商以确定是否必须更新扩展。

### Elasticsearch

升级到2.4.0之前，必须安装并配置Elasticsearch7.6或更高版本或OpenSearch 1.2。Adobe不再支持Elasticsearch2.x、5.x和6.x。

请参阅 [升级Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有关在部署到生产之前备份数据、检测潜在迁移问题和测试升级的完整说明。 根据您当前版本的Elasticsearch，可能需要或不需要完全重新启动群集。

Elasticsearch需要JDK 1.8或更高版本。 请参阅 [安装Java软件开发工具包(JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 以检查安装的JDK版本。

[配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 介绍在将Elasticsearch2更新到支持的版本后必须执行的任务。

### OpenSearch

OpenSearch是Elasticsearch7.10.2的开源分支，在Elasticsearch进行许可更改后。 以下版本的Adobe Commerce和Magento Open Source引入了对OpenSearch的支持：

- 2.4.4
- 2.4.3-p2
- 2.3.7-p3

您可以 [从Elasticsearch迁移到OpenSearch](opensearch-migration.md) 仅当您升级到上面列出的Adobe Commerce或Magento Open Source版本（或更高版本）时。

OpenSearch需要JDK 1.8或更高版本。 请参阅 [安装Java软件开发工具包(JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 以检查安装的JDK版本。

[配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 描述更改搜索引擎后必须执行的任务。

### 第三方扩展

我们建议您联系搜索引擎供应商以确定您的扩展是否与2.4完全兼容。

## 设置打开的文件限制

设置打开文件限制(ulimit)有助于避免因多次递归调用长查询字符串而失败或使用 `bin/magento setup:rollback` 命令。 此命令对于不同的UNIX壳不同。 有关 `ulimit` 命令。

Adobe建议设置打开的文件 [ulimit](https://ss64.com/bash/ulimit.html) 值 `65536` 或更多，但您可以根据需要使用更大的值。 您可以在命令行中设置上限，也可以将其设为用户Shell的永久设置。

要从命令行设置上限，请执行以下操作：

1. 切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 将上限设置为65536。

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > 打开文件ulimit的语法取决于您使用的UNIX shell。 上述设置应与CentOS和Ubuntu一起使用，与Bash shell配合使用。 但是，对于Mac OS，正确的设置是ulimit -S 65532。 有关更多信息，请参阅手册页或操作系统参考。

要在Bash Shell中设置值，请执行以下操作：

1. 切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 打开 `/home/<username>/.bashrc` 在文本编辑器中。
1. 添加以下行：

   ```bash
   ulimit -s 65536
   ```

1. 保存对 `.bashrc` 并退出文本编辑器。

>[!IMPORTANT]
>
>我们建议您避免为 `pcre.recursion_limit` 属性 `php.ini` 文件，因为它可能导致不完整的回滚，且没有失败通知。

## 验证cron作业是否正在运行

UNIX任务调度程序 `cron` 对于日常Adobe Commerce和Magento Open Source操作至关重要。 它会计划一些事项，例如重新索引、新闻稿、电子邮件、Sitemap等。 有几项功能需要至少运行一个cron作业作为文件系统所有者。

要验证cron作业是否设置正确，请输入以下命令作为文件系统所有者来检查crontab:

>[!NOTE]
>
>crontab是负责运行cron作业的配置文件。

```bash
crontab -l
```

应显示与以下内容类似的结果：

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

未运行cron的另一个症状是管理员中出现以下错误：

![](../../assets/upgrade-guide/cron-not-running.png)

要查看错误，请单击 **系统消息** 窗口顶部的，如下所示：

![](../../assets/upgrade-guide/system-messages.png)

请参阅 [配置并运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 。

## 设置DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4包含安全增强功能，这些功能要求将一些数据从序列化转换为JSON。 此转换在升级期间进行，并且可能需要很长时间，具体取决于数据库中的数据数量。

下表受到的影响最大：

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

如果您有大量数据，则可以通过设置环境变量的值来提高性能。 `DATA_CONVERTER_BATCH_SIZE`. 默认情况下，该值设置为 `50,000`.

要设置环境变量，请执行以下操作：

1. 切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 设置变量：

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` 需要内存；请避免先将其设置为大值（约1 GB），而无需对其进行测试。

1. 升级完成后，您可以取消设置变量：

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 验证文件系统权限

出于安全考虑，Adobe Commerce和Magento Open Source需要对文件系统拥有特定权限。 权限与 _[所有权](https://devdocs.magento.com/guides/v2.4/comp-mgr/prereq/prereq_compman-checklist.html#magento-owner-group)_. 所有权决定了谁可以在文件系统上执行操作；权限决定了用户可以执行的操作。

文件系统中的目录必须由 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) 群组。

要验证文件系统权限设置是否正确，请登录到应用程序服务器，或使用托管提供商的文件管理器应用程序。

例如，如果应用程序安装在 `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

示例输出：

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

有关示例输出的说明，请参阅以下内容：

- 大多数文件 `-rw-rw----`，其中 `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- 文件系统所有者是 `magento_user`

要获取更多详细信息，可输入以下命令：

```bash
ls -la /var/www/html/magento2/pub
```

因为Adobe Commerce和Magento Open Source会将静态文件资产部署到的子目录 `pub`，则最好也在此处验证权限和所有权。

有关更多信息，请参阅 [文件系统权限和所有权](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

## 设置 `pub/` 目录根目录

请参阅 [修改docroot以提高安全性](https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html) 以了解更多详细信息。

## 安装编辑器更新插件

的 [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) 编辑器插件可解析必须对根项目所做的更改 `composer.json` 文件，然后才能更新到新产品要求。

该插件通过识别并帮助您解决依赖关系冲突，而不是要求您手动识别和修复这些冲突，从而部分自动执行手动升级。

要安装插件，请执行以下操作：

1. 将包添加到 `composer.json` 文件。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 更新依赖项：

   ```bash
   composer update
   ```
