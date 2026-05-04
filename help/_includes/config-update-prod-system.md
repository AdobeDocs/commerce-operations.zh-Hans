---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 更新生产系统

**要更新生产系统**：

1. 以文件系统所有者的身份登录到生产系统。
1. 更改为应用程序根并启用维护模式。

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   有关其他选项，例如设置IP地址白名单的功能，请参阅[`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md)。

1. 通过将`app/etc/env.php`中的`cron_run`设置为`false`停止任何正在运行的队列工作程序，如下所示：

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 更新配置。

   ```shell
   bin/magento app:config:import
   ```

1. 最后，`kill`任何活动的使用者进程。

   ```shell
   kill <PID>
   ```

   其中`PID`是要终止的进程ID，例如：

   ```shell
   kill 1234
   ```

1. 从源代码管理中提取代码。

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. 更新配置。

   ```shell
   bin/magento app:config:import
   ```

1. 清理缓存。

   ```shell
   bin/magento cache:clean
   ```

1. 结束维护模式。

   ```shell
   bin/magento maintenance:disable
   ```
