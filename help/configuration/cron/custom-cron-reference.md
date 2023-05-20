---
title: 自訂cron工作和cron群組參考
description: 瞭解如何使用cron群組自訂cron。
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 自訂crons參考

此主題可協助您為自訂模組設定crontab和選擇性cron群組。 如果您的自訂模組需要定期排程工作，您必須為該模組設定crontab。 A _crontab_ 是cron工作設定。

您可以視需要設定自訂群組，讓您可以獨立於其他cron工作，執行在該群組中定義的cron工作。

如需逐步教學課程，請參閱 [設定自訂cron作業和cron群組（教學課程）](custom-cron-tutorial.md).

如需cron作業的概觀，請參閱 [設定cron工作](../cli/configure-cron-jobs.md).

## 設定cron群組

本節探討如何選擇為自訂模組建立cron群組。 如果您不需要這樣做，請繼續下一節。

A _cron組_ 是一個邏輯群組，可讓您一次輕鬆執行多個處理程式的cron。 大部分的Commerce模組都使用 `default` cron群組；有些模組會使用 `index` 群組。

如果您要為自訂模組實作cron，則可以選擇使用 `default` 群組或其他群組。

**若要為模組設定cron群組**：

建立 `crontab.xml` 模組目錄中的檔案：

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

對於一個群組，檔案應具有以下內容：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

其中：

| 值 | 說明 |
|---|---|
| `group_name` | cron群組的名稱。 群組名稱不必是唯一的。 您可以一次為一個群組執行cron。 |
| `job_name` | 此cron作業的唯一ID。 |
| `classpath` | 要具現化的類別（類別路徑）。 |
| `method` | 中的方法 `classpath` 以呼叫。 |
| `time` | 以cron格式排程。 如果排程定義於Commerce資料庫或其他儲存體中，請省略此引數。 |

產生的結果 `crontab.xml` 有兩個群組，看起來可能像這樣：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

如需範例，請參閱 [Magento_客戶crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### 指定Cron群組選項

您可以透過以下方式宣告新群組並指定其設定選項（所有選項都會在存放區檢視範圍內執行）： `cron_groups.xml` 檔案，位於：

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

以下範例說明 `cron_groups.xml` 檔案：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
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

其中：

| 選項 | 說明 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | 排程寫入的頻率（以分鐘為單位） `cron_schedule` 表格。 |
| `schedule_ahead_for` | 將排程寫入「 」的提前時間（以分鐘為單位） `cron_schedule` 表格。 |
| `schedule_lifetime` | cron工作必須開始或認為cron工作已錯過的時間範圍（以分鐘為單位）（「太晚了」而無法執行）。 |
| `history_cleanup_every` | cron記錄保留在資料庫中的時間（分鐘）。 |
| `history_success_lifetime` | 成功完成的cron工作記錄保留在資料庫中的時間（分鐘）。 |
| `history_failure_lifetime` | 失敗的cron作業記錄保留在資料庫中的時間（以分鐘為單位）。 |
| `use_separate_process` | 在單獨的php程式中執行此cron群組的工作 |

## 停用cron工作

Cron工作沒有 `disable` 功能與我們的相同， [觀察者](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). 但是，可以使用以下技術停用cron作業： `schedule` 包含永不發生之日期的時間。

例如，停用 `visitor_clean` cron工作，定義於 `Magento_Customer` 模組：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

若要停用 `visitor_clean` cron工作，建立自訂模組並重寫 `visitor_clean` cron工作 `schedule`：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

現在， `visitor_clean` cron工作已設定在2月30日的00:00執行 — 絕不會發生的日期。
