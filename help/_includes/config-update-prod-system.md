---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---
# 更新生产系统

**更新生产系统**:

1. 以文件系统所有者身份登录到生产系统。
1. 更改为应用程序根并启用维护模式。

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   有关其他选项（如设置IP地址白名单的功能），请参阅 [`magento maintenance:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. 通过设置 `cron_run` to `false` in `app/etc/env.php` 如下所示：

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 更新配置。

   ```bash
   bin/magento app:config:import
   ```

1. 最后， `kill` 任何活动客户进程。

   ```bash
   kill <PID>
   ```

   其中 `PID` 是要终止的进程ID，例如：

   ```bash
   kill 1234
   ```

1. 从源代码管理中提取代码。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 更新配置。

   ```bash
   bin/magento app:config:import
   ```

1. 清除缓存。

   ```bash
   bin/magento cache:clean
   ```

1. 结束维护模式。

   ```bash
   bin/magento maintenance:disable
   ```