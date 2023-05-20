---
title: 移轉概述
description: 瞭解如何透過開始將資料從Magento1移轉至Magento2 [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 移轉概述

開始移轉之前，請停止所有Magento1 cron工作。

在移轉程式中，請遵循下列一般規則才能成功移轉：

1. **不要** 在「Magento1管理員」中進行變更，但訂單管理除外（出貨、建立商業發票及銷退折讓單）
1. **不要** 變更任何程式碼
1. **不要** 在Magento2管理員和店面中進行變更

>[!TIP]
>
>允許Magento1店面中的所有操作。

## 執行 [!DNL Data Migration Tool]

本節說明如何執行 [!DNL Data Migration Tool] 移轉設定、資料或增量變更。

### 首要步驟

1. 以具有寫入檔案系統許可權的使用者身分登入應用程式伺服器，或切換至該使用者。 另請參閱 [切換到檔案系統擁有者](../../../installation/prerequisites/file-system/overview.md).

   如果您使用bash shell，則可以使用以下語法切換到檔案系統擁有者並同時輸入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果檔案系統擁有者不允許登入，您可以執行下列動作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 若要從任何目錄執行Magento命令，請新增 `<magento_root>/bin` 至您的系統 `PATH`.

   由於shell的語法不同，請參考參考如 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS的bash shell範例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   您可以選擇以下列方式執行命令：

   - `cd <magento_root>/bin` 並以下列身分執行 `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` 是網頁伺服器docroot的子目錄。

### 命令語法

以下是典型的命令範例：

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

- `<mode>` 可以是： [`settings`](settings.md)， [`data`](data.md)，或 [`delta`](delta.md)
- `[-r|--reset]` 是從頭開始移轉的可選引數。 您可以使用此引數來測試移轉。
- `[-a|--auto]` 是選用引數，可防止移轉在遇到完整性檢查錯誤時停止。
- `{<path to config.xml>}` 為的絕對檔案系統路徑 `config.xml`；此引數為必要項。

>[!NOTE]
>
>記錄檔會寫入 `<magento_root>/var/` 目錄。


## 移轉順序

當我們建立 [!DNL Data Migration Tool]，我們假設了下列資料傳輸順序：

1. [設定](settings.md)
1. [資料](data.md)
1. [變更](delta.md)

我們強烈建議您以相同的順序移轉資料。
