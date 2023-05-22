---
title: 還原分割資料庫
description: 從已棄用的分割資料庫實作還原為單一資料庫實作。
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 從分割資料庫還原

{{ee-only}}

針對已實作的Adobe Commerce客戶 [分割資料庫](multi-master.md)，下列主題說明如何回覆或移回單一資料庫。 我們建議目前使用Split Database的Adobe Commerce商家，並計畫升級至2.4.2和更新版本，檢閱這些步驟，以及我們的 [宣告](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 已計畫棄用分割資料庫的相關資訊。

從分割資料庫回覆至單一資料庫時，需要建立 `magento_quote` 和 `magento_sales` 將資料庫載入單一資料庫之前 `magento_main` 資料庫。

在此範例中，我們會登入安裝在相同主機上的全部三個資料庫(`magento2-mysql`)作為「root」使用者。 您必須將這些值取代為您的資料庫適當的值。

1. 建立備份 `magento_quote` 資料庫：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 建立備份 `magento_sales` 資料庫：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. 載入 `magento_quote` 將資料庫移入 `magento_main` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. 載入 `magento_sales` 將資料庫移入 `magento_main` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 放下 `magento_sales` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 放下 `magento_quote` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 移除的部署設定 `checkout` 和 `sales` 在 `connections` 和 `resources` 的區段 `env.php` 檔案。
1. 還原外部索引鍵：

   ```bash
   bin/magento setup:upgrade
   ```

## 驗證您的工作

若要驗證您的單一資料庫實作是否正常運作，請執行以下工作，並確認已將資料新增至 `magento_main` 使用資料庫工具(如 [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin)：

1. 確認外部金鑰已還原。 例如， `QUOTE_STORE_ID_STORE_STORE_ID` 中的索引鍵 `quote` 資料庫表格。
1. 確認客戶可以從店面下訂單。
1. 確認在將分割資料庫還原為單一資料庫之前建立的訂單可在Admin中使用。
