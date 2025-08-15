---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 更新生产系统

**要更新生产系统**：

1. 以文件系统所有者的身份登录到生产系统。
1. 更改为应用程序根并启用维护模式。

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   有关其他选项，例如设置IP地址白名单的功能，请参阅[`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md)。

1. 通过将`cron_run`中的`false`设置为`app/etc/env.php`停止任何正在运行的队列工作程序，如下所示：

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 更新配置。

   ```bash
   bin/magento app:config:import
   ```

1. 最后，`kill`任何活动的使用者进程。

   ```bash
   kill <PID>
   ```

   其中`PID`是要终止的进程ID，例如：

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

1. 清理缓存。

   ```bash
   bin/magento cache:clean
   ```

1. 结束维护模式。

   ```bash
   bin/magento maintenance:disable
   ```
