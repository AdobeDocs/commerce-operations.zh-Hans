---
title: 設定並執行cron工作
description: 瞭解如何管理cron工作。
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# 設定cron工作

{{file-system-owner}}

有些Commerce功能至少需要一個cron工作，這會安排未來發生的活動。 以下是這些活動的部分清單：

- 目錄價格規則
- 電子報
- 產生Google Sitemap
- 客戶警示/通知（產品價格變更、產品補貨）
- 重新索引
- 私人銷售(僅限Adobe Commerce)
- 自動更新匯率
- 所有Commerce電子郵件（包括訂單確認和異動）

>[!WARNING]
>
>您無法再執行 `dev/tools/cron.sh` 因為指令碼已移除。

>[!INFO]
>
>Commerce仰賴許多重要系統功能的正確cron工作設定，包括編制索引。 若未正確設定，表示Commerce將無法如預期運作。

UNIX系統使用 _crontab_，此檔案包含對cron精靈的指示，指示精靈在「這個日期這個時間執行此命令」。 每個使用者都有自己的crontab，而且任何指定crontab中的命令都會以擁有該命令的使用者身分執行。

若要在網頁瀏覽器中執行cron，請參閱 [在瀏覽器中執行安全的cron.php](../security/secure-cron-php.md).

## 建立或移除Commerce crontab

本節討論如何建立或移除您的Commerce crontab （即Commerce cron作業的設定）。

此 _crontab_ 是用於執行cron作業的設定。

Commerce應用程式使用能以不同設定執行的cron任務。 PHP命令列配置控制一般cron作業，該作業會重新索引索引器、產生電子郵件、產生Sitemap等等。

>[!WARNING]
>
>- 為避免在安裝和升級期間出現問題，強烈建議您將相同的PHP設定套用到PHP命令列配置和PHP Web伺服器外掛程式的配置。 如需詳細資訊，請參閱 [必要的PHP設定](../../installation/prerequisites/php-settings.md).
>- 在多節點系統中，crontab只能在一個節點上執行。 唯有因效能或擴充性相關原因而設定多個Webnode時，才能使用此功能。


### 建立Commerce crontab

從2.2版開始，Commerce會為您建立crontab。 我們會將Commerce crontab新增至Commerce檔案系統擁有者的任何已設定crontab。 換言之，如果您已設定其他擴充功能或應用程式的crontab，我們會將Commerce crontab新增至擴充功能或應用程式。

商務crontab在裡面 `#~ MAGENTO START` 和 `#~ MAGENTO END` 評論您的簡訊。

若要建立Commerce crontab：

1. 登入為，或切換至 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 變更至Commerce安裝目錄。
1. 輸入下列命令：

   ```bash
   bin/magento cron:install [--force]
   ```

使用 `--force` 重寫現有的crontab。

>[!INFO]
>
>- `magento cron:install` 不會重寫內部的現有crontab `#~ MAGENTO START` 和 `#~ MAGENTO END` 評論您的簡訊。
>- `magento cron:install --force` 對Commerce評論以外的任何cron工作沒有影響。


若要檢視crontab，請輸入下列命令作為檔案系統擁有者：

```bash
crontab -l
```

範例如下：

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>此 `update/cron.php` 檔案已在Commerce 2.4.0中移除，若此檔案存在於您的安裝中，則可安全地將其移除。
>
>任何參考 `update/cron.php` 和 `bin/magento setup:cron:run` 應該也會從crontab中移除&#39;

### 移除Commerce crontab

您應僅在解除安裝Commerce應用程式之前移除Commerce crontab。

移除Commerce crontab：

1. 以身分登入或切換至 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 變更至Commerce安裝目錄。
1. 輸入下列命令：

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>這個命令對外部的cron工作沒有影響 `#~ MAGENTO START` 和 `#~ MAGENTO END` 評論您的簡訊。

## 從命令列執行cron

命令選項：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

位置 `--group` 指定要執行的cron群組（省略此選項即可為所有群組執行cron）

若要執行索引cron工作，請輸入：

```bash
bin/magento cron:run --group index
```

若要執行預設的cron工作，請輸入：

```bash
bin/magento cron:run --group default
```

若要設定自訂cron作業和群組，請參閱 [設定自訂cron作業和cron群組](../cron/custom-cron.md).

>[!INFO]
>
>您必須執行兩次cron：第一次探索要執行的任務，第二次執行任務本身。 第二個cron回合必須發生在或晚於 `scheduled_at` 每個任務所需的時間。

## 記錄

全部 `cron` 工作資訊已移出 `system.log` 放入個別 `cron.log`.
根據預設，cron資訊可在以下網址找到： `<install_directory>/var/log/cron.log`.
cron工作的所有例外狀況記錄者 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

除了登入之外 `cron.log`：

- 失敗的工作具有 `ERROR` 和 `MISSED` 狀態會記錄到 `<install_directory>/var/log/support_report.log`.

- 具有「 」的工作 `ERROR` 狀態一律記錄為 `CRITICAL` 在 `<install_directory>/var/log/exception.log`.

- 具有的工作 `MISSED` 狀態記錄為 `INFO` 在 `<install_directory>/var/log/debug.log` 目錄（僅限開發人員模式）。

>[!INFO]
>
>所有cron資料也會寫入 `cron_schedule` 表格。 此表格提供cron工作的歷史記錄，包括：
>
>- 工作ID和代碼
>- 狀態
>- 建立日期
>- 排程日期
>- 執行日期
>- 完成日期
>
>若要檢視表格中的記錄，請在命令列上登入Commerce資料庫並輸入 `SELECT * from cron_schedule;`.
