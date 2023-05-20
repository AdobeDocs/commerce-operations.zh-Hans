---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 更新生產系統

**更新生產系統的方式**：

1. 以檔案系統擁有者的身分登入生產系統。
1. 變更為應用程式根並啟用維護模式。

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   如需其他選項（例如設定IP位址白名單的功能），請參閱 [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. 透過設定停止任何執行中的佇列背景工作 `cron_run` 至 `false` 在 `app/etc/env.php` 如下所示：

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 更新設定。

   ```bash
   bin/magento app:config:import
   ```

1. 最後， `kill` 任何作用中的消費者程式。

   ```bash
   kill <PID>
   ```

   位置 `PID` 是要終止的程式ID，例如：

   ```bash
   kill 1234
   ```

1. 從原始檔控制提取程式碼。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 更新設定。

   ```bash
   bin/magento app:config:import
   ```

1. 清除快取。

   ```bash
   bin/magento cache:clean
   ```

1. 結束維護模式。

   ```bash
   bin/magento maintenance:disable
   ```
