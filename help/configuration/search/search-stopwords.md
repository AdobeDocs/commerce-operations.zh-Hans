---
title: 設定搜尋停用詞
description: 瞭解如何使用CSV檔案管理Adobe Commerce的停用詞。
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 設定搜尋停用詞

一般而言， _停用詞_ 是搜尋引擎在處理文字後篩選掉的常見字詞。 最初，當磁碟空間和記憶體非常有限時，每儲存KB就意味著效能大幅提升。 因此，搜尋引擎透過忽略特定字詞並維持較小的索引而獲得效能提升。

雖然我們目前擁有更多儲存空間，但效能仍很重要。 Elasticsearch和OpenSearch與其他搜尋引擎一樣，仍使用停用字詞來改善效能。

您必須使用位於以下位置的CSV檔案管理停用詞： `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄或 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` 目錄（視您安裝Commerce軟體的方式而定）。

如需Elasticsearch和OpenSearch如何使用停用字詞的詳細資訊，請參閱下列資源：

- [停用詞：效能與精確度](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [停用字詞的利弊](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [使用停用詞](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [停用字詞和效能](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 設定停用詞

停用字詞位於 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄。 Adobe Commerce和Magento Open Source隨附一個CSV檔案，其中包含預設地區設定的停用詞，以及另一個檔案 `stopwords.csv`，其中包含其他CSV檔案所未代表之任何地區設定的停用詞。

停用字檔案快取的預設存留期為15分鐘。

### 編輯現有地區設定的停用詞

**若要編輯停用詞**：

1. 登入您的Commerce伺服器，或切換至 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 使用文字編輯器開啟中的停用字檔案 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄。

   CSV檔案使用命名慣例 `stopwords_<locale_code>.csv`. 例如，德文停用字檔案命名為 `stopwords_de_DE.csv`.

1. 在檔案中新增單字、移除單字或變更單字。

   （檔案中的每個停用字都會從新行開始。）

1. 儲存變更並退出文字編輯器。
1. 清除設定快取。

   - 管理員： **系統** >工具> **快取管理**. 選取 **設定** 核取方塊，並在上方清單中按一下 **重新整理**. 按一下 **提交** 以完成動作。

   - 命令列：以檔案系統擁有者的身分，輸入下列命令：

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. 在您的店面搜尋辭彙以檢查結果。

### 建立新地區設定的停用詞

**為地區設定新增停用詞**：

1. 登入您的Commerce伺服器，或切換至 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).

1. 使用文字編輯器建立名為的停用字檔案 `stopwords_<locale_code>.csv` 在 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄。

   例如，若要建立義大利語地區設定的停用詞，請為檔案命名 `stopwords_it_IT.csv`.

1. 在非索引字檔案中，確定每個非索引字都位於單獨的行上。
1. 儲存變更並退出文字編輯器。
1. 在同一目錄中，開啟 `esconfig.xml` 在文字編輯器中。
1. 新增行至 `esconfig.xml` 如下所示：

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例如，若要新增義大利語停用字檔案，請新增下列行：

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 將變更儲存至 `esconfig.xml` 並退出文字編輯器。
1. 清除設定快取。

   - 管理員： **系統** >工具> **快取管理**. 選取 **設定** 核取方塊，並在上方清單中按一下 **重新整理**. 按一下 **提交** 以完成動作。

   - 命令列：以檔案系統擁有者的身分，輸入下列命令：

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. 在您的店面搜尋辭彙以檢查結果。

## 變更停用字目錄

本節討論如何選擇性地從下列其中一項變更預設停用字目錄：

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

位置取決於您安裝Commerce軟體的方式。 如果您複製Magento2 GitHub存放庫，路徑位於 `app/code`. 如果您已安裝壓縮封存或中繼資料，路徑會位於 `vendor`.

**變更目錄**：

1. 以檔案系統擁有者的身分，開啟Elasticsearch `di.xml` 在文字編輯器中。

   如果您複製存放庫，則該存放庫位於 `app/code/Magento/Elasticsearch/etc/di.xml`

   如果您有封存或中繼資料，則位於 `vendor/magento/module-elasticsearch/etc/di.xml`

1. 變更值 `stopwordsDirectory` 至所需的目錄：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 將變更儲存至 `di.xml` 並退出文字編輯器。

## 若要從模組變更目錄

1. [建立模組](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 在您的模組中 `etc/di.xml` 新增指示：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 在您的模組中，建立目錄 `etc/stopwords`，以及對應的CSV檔案。

1. 將變更儲存至 `di.xml` 並退出文字編輯器。
