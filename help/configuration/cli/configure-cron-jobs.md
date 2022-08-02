---
title: 配置和运行cron作业
description: 了解如何管理cron作业。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# 配置cron作业

{{file-system-owner}}

一些“商务”功能至少需要一个cron作业，该作业会安排将来的活动。 这些活动的部分列表如下：

- 目录价格规则
- 新闻稿
- 生成Google站点地图
- 客户警报/通知（产品价格变动，产品退回现货）
- 重新索引
- 私人销售(仅限Adobe Commerce)
- 货币汇率的自动更新
- 所有商务电子邮件（包括订单确认和交易电子邮件）

>[!WARNING]
>
>您无法再运行 `dev/tools/cron.sh` 因为脚本已被删除。

>[!INFO]
>
>商务依赖于许多重要系统功能（包括索引）的正确cron作业配置。 未正确设置它意味着商务将无法按预期运行。

UNIX系统使用 _crontab_，该文件包含对cron守护程序的指令，该指令告知该守护程序“在此日期的此时运行此命令”。 每个用户都有其自己的crontab，任何给定crontab中的命令都将作为拥有它的用户执行。

要在Web浏览器中运行cron，请参阅 [确保在浏览器中运行cron.php](../security/secure-cron-php.md).

## 创建或删除Commerce crontab

本节讨论如何创建或删除您的Commerce crontab（即Commerce cron作业的配置）。

的 _crontab_ 是用于运行cron作业的配置。

商务应用程序使用可以通过不同配置运行的cron任务。 PHP命令行配置控制用于重新索引器、生成电子邮件、生成站点地图等的常规cron作业。

>[!WARNING]
>
>- 为避免在安装和升级过程中出现问题，我们强烈建议您将相同的PHP设置应用于PHP命令行配置和PHP Web服务器插件的配置。 有关更多信息，请参阅 [所需的PHP设置](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).
>- 在多节点系统中， crontab只能在一个节点上运行。 仅当您出于与性能或可扩展性相关的原因设置了多个Web节点时，这才适用于您。


### 创建商务crontab

从版本2.2开始，Commerce会为您创建一个crontab。 我们将Commerce crontab添加到Commerce文件系统所有者的任何已配置的crontab中。 换言之，如果您已经为其他扩展或应用程序设置了crontab，则会向其添加Commerce crontab。

Commerce crontab位于内部 `#~ MAGENTO START` 和 `#~ MAGENTO END` 评论。

要创建商务crontab，请执行以下操作：

1. 以登录方式登录，或切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 更改为Commerce安装目录。
1. 输入以下命令：

   ```bash
   bin/magento cron:install [--force]
   ```

使用 `--force` 重写现有crontab。

>[!INFO]
>
>- `magento cron:install` 不重写内部的现有crontab `#~ MAGENTO START` 和 `#~ MAGENTO END` 评论。
>- `magento cron:install --force` 对“商务”评论之外的任何cron作业都不起作用。


要查看crontab，请输入以下命令作为文件系统所有者：

```bash
crontab -l
```

示例如下：

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>的 `update/cron.php` 文件已在Commerce 2.4.0中删除，如果此文件存在于您的安装中，则可以安全地将其删除。
>
>对 `update/cron.php` 和 `bin/magento setup:cron:run` 也应从crontab&#39;中删除

### 删除Commerce crontab

只有在卸载Commerce应用程序之前，才应删除Commerce crontab。

要删除Commerce crontab，请执行以下操作：

1. 登录方式或切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 更改为Commerce安装目录。
1. 输入以下命令：

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>此命令对 `#~ MAGENTO START` 和 `#~ MAGENTO END` 评论。

## 从命令行中运行cron

命令选项：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

where `--group` 指定要运行的cron组（忽略此选项为所有组运行cron）

要运行索引cron作业，请输入：

```bash
bin/magento cron:run --group index
```

要运行默认的cron作业，请输入：

```bash
bin/magento cron:run --group default
```

要设置自定义cron作业和组，请参阅 [配置自定义cron作业和cron组](../cron/custom-cron.md).

>[!INFO]
>
>您必须运行两次cron:第一次发现要运行的任务，第二次发现要自己运行任务。 第二次cron运行必须在 `scheduled_at` 每项任务的时间。

## 记录

全部 `cron` 作业信息已从 `system.log` 分隔 `cron.log`.
默认情况下，可在 `<install_directory>/var/log/cron.log`.
cron作业的所有例外都由 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

除了登录之外 `cron.log`:

- 失败的作业 `ERROR` 和 `MISSED` 状态已记录到 `<install_directory>/var/log/support_report.log`.

- 使用 `ERROR` 状态始终记录为 `CRITICAL` in `<install_directory>/var/log/exception.log`.

- 使用 `MISSED` 状态记录为 `INFO` 在 `<install_directory>/var/log/debug.log` 目录（仅限开发人员模式）。

>[!INFO]
>
>所有CRON数据也会写入 `cron_schedule` 表。 该表提供了cron作业的历史记录，包括：
>
>- 作业ID和代码
>- 状态
>- 创建日期
>- 计划日期
>- 执行日期
>- 完成日期
>
>要查看表中的记录，请登录命令行上的Commerce数据库，然后输入 `SELECT * from cron_schedule;`.
