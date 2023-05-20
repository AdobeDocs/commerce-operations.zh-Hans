---
title: 設定自訂cron工作和cron群組（教學課程）
description: 使用此逐步教學課程來建立自訂cron工作。
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# 設定自訂cron工作

此逐步教學課程說明如何在範例模組中建立自訂cron工作以及選用的cron群組。 您可以使用已擁有的模組，也可以使用我們的範例模組 [`magento2-samples` 存放庫][samples].

執行cron工作會導致將一列新增到 `cron_schedule` 具有cron作業名稱的表格， `custom_cron`.

我們也會說明如何選擇性建立cron群組，以便使用商業應用程式預設值以外的設定來執行自訂cron工作。

在本教學課程中，我們假設以下事項：

- 商務應用程式安裝在 `/var/www/html/magento2`
- 您的Commerce資料庫使用者名稱和密碼都是 `magento`
- 您以「 」身分執行所有動作 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)

## 步驟1：取得範例模組

若要設定自訂cron工作，您需要範例模組。 我們建議 `magento-module-minimal` 模組。

如果您已經有範例模組，可以使用它；跳過此步驟和下一個步驟，並繼續步驟3：建立類別以執行cron。

**取得範例模組的方式**：

1. 以或切換為身分登入您的Commerce伺服器， [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 變更至不在Commerce應用程式根目錄中的目錄（例如主目錄）。
1. 原地複製 [`magento2-samples` 存放庫][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   如果命令失敗並出現錯誤 `Permission denied (publickey).`，您必須 [將您的SSH公開金鑰新增至GitHub.com][git-ssh].

1. 建立要將範常式式碼複製到其中的目錄：

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 複製範例模組程式碼：

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 確認檔案已正確複製：

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   您應該會看到下列結果：

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. 更新Commerce資料庫和結構描述：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

## 步驟2：驗證範例模組

繼續之前，請確認範例模組已註冊並啟用。

1. 執行以下命令：

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. 確認模組已啟用。

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>如果輸出指示 `Module does not exist`，檢閱 [步驟1](#step-1-get-a-sample-module) 請小心。 確定您的程式碼位於正確的目錄中。 拼字與大小寫很重要；如果有任何差異，則不會載入模組。 此外，別忘了執行 `magento setup:upgrade`.

## 步驟3：建立類別以執行cron

此步驟顯示建立cron作業的簡單類別。 類別只會將一列寫入至 `cron_schedule` 確認其設定成功的表格。

若要建立類別，請執行下列動作：

1. 為類別建立目錄，並變更至該目錄：

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. 已建立名為的檔案 `Test.php` 目錄中包含下列內容：

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## 步驟4：建立 `crontab.xml`

此 `crontab.xml` 檔案會設定執行自訂cron程式碼的排程。

建立 `crontab.xml` 如下所示 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` 目錄：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

先前 `crontab.xml` 執行 `Magento/SampleMinimal/Cron/Test.php` 每分鐘會分類一次，結果會將一列新增至 `cron_schedule` 表格。

若要讓cron排程可從管理員設定，請使用系統設定欄位的設定路徑。

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

其中， `system/config/path` 是中定義的系統設定路徑 `etc/adminhtml/system.xml` 模組的。

## 步驟5：編譯和快取清除

使用以下命令編譯程式碼：

```bash
bin/magento setup:di:compile
```

並使用以下命令清除快取：

```bash
bin/magento cache:clean
```

## 步驟6：驗證cron工作

此步驟顯示如何在上使用SQL查詢來成功驗證自訂cron作業。 `cron_schedule` 資料庫表格。

驗證cron：

1. 執行Commerce cron工作：

   ```bash
   bin/magento cron:run
   ```

1. 輸入 `magento cron:run` 命令兩或三次。

   第一次輸入命令時，它會排入工作佇列；接著，就會執行cron工作。 您必須輸入指令 _至少_ 兩次。

1. 執行SQL查詢 `SELECT * from cron_schedule WHERE job_code like '%custom%'` 如下所示：

   1. 輸入 `mysql -u magento -p`
   1. 在 `mysql>` 提示，輸入 `use magento;`
   1. 輸入 `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      結果應類似於以下內容：

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. （選用）確認訊息已寫入Commerce的系統記錄檔：

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   您應該會看到一或多個類似下列的專案：

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   這些訊息來自 `execute` 中的方法 `Test.php`：

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

如果SQL命令和系統記錄檔不包含任何專案，請執行 `magento cron:run` 再命令幾次，然後等待。 更新資料庫可能需要一些時間。

## 步驟7 （選用）：設定自訂cron群組

此步驟顯示如何選擇性設定自訂cron群組。 如果您希望自訂cron工作以與其他cron工作不同的排程執行（通常每分鐘執行一次），或如果您希望多個自訂cron工作以不同的設定執行，則應設定自訂cron群組。

若要設定自訂cron群組：

1. 開啟 `crontab.xml` 在文字編輯器中。
1. 變更 `<group id="default">` 至 `<group id="custom_crongroup">`
1. 退出文字編輯器。
1. 建立 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` 包含下列內容：

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

如需選項含義的說明，請參閱 [自訂crons參考](custom-cron-reference.md).

## 步驟8：驗證您的自訂cron群組

此 _可選_ 步驟顯示如何使用管理員驗證您的自訂cron群組。

若要驗證您的自訂cron群組：

1. 為您的自訂群組執行Commerce cron工作：

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   至少執行命令兩次。

1. 清除快取：

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 以管理員身分登入管理員。
1. 按一下 **商店** > **設定** > **設定** > **進階** > **系統**.
1. 在右窗格中，展開 **Cron**.

   您的cron群組顯示如下：

   ![您的自訂cron群組](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
