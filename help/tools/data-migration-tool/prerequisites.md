---
title: '''[!DNL Data Migration Tool] 必備條件'
description: 瞭解在開始使用之前需要做什麼 [!DNL Data Migration Tool] 以在Magento1和Magento2之間傳輸資料。
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 必備條件

開始移轉之前，請確定符合下列需求。

## Magento2系統

* 設定您的Magento2系統，使其符合 [系統需求](../../installation/system-requirements.md).

   使用至少符合您現有Magento1系統的拓撲和設計。

* [安裝Magento2](../../installation/overview.md).

## Cron

不要開始Magento2 cron工作。

## 資料庫

* 安裝後，請備份或 [傾印](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) 您的Magento2資料庫。 這可讓您在移轉失敗時還原初始資料庫狀態。

* 驗證 [!DNL Data Migration Tool] 具有網路存取權，可連線Magento1和Magento2資料庫。

   開啟防火牆中的連線埠，讓移轉工具可以與資料庫通訊。

* 請確定您的MySQL帳戶擁有存取Magento資料庫的所有必要許可權。

如果您的Magento1資料庫已啟用二進位記錄，請設定全域 [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL系統變數至 `1`，或授予 [SUPER許可權](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) 至您的帳戶。

* 我們不建議在移轉前在您的Magento2存放區中建立新實體（產品、類別和屬性），因為 [!DNL Data Migration Tool] 以Magento1中的舊實體覆寫此類新實體。

## 擴充功能

將Magento1擴充功能代碼移轉至Magento2。

若要尋找最新的擴充功能版本，請造訪 [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) 或連絡您的擴充功能提供者。

您也可以使用 [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
