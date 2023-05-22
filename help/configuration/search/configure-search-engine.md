---
title: 搜尋引擎設定
description: 設定Adobe Commerce和Magento Open Source內部部署的搜尋引擎。
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 搜尋引擎設定

本節討論測試Elasticsearch或OpenSearch與Adobe Commerce和Magento Open Source內部部署所需的最低設定。

>[!TIP]
>
>在2.4.4版和2.4.3-p2版中，所有欄位都標示為 **Elasticsearch** 也適用於OpenSearch。
>當版本2.4.6中引入Elasticsearch8.x支援時，已建立新標籤以區分Elasticsearch和OpenSearch設定。

如需設定搜尋引擎的詳細資訊，請參閱 [使用手冊](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## 從管理員設定搜尋引擎

>[!TIP]
>
>如需升級至新搜尋引擎版本的指示，請參閱 [升級必備條件](../../upgrade/prepare/prerequisites.md).

若要設定您的系統以使用Elasticsearch或OpenSearch：

1. 以管理員身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 從 **[!UICONTROL Search Engine]** 清單中，選取搜尋引擎的對應版本。

   下表列出設定和測試與Commerce的連線所需的選項。 除非您變更搜尋引擎的伺服器設定，否則預設值應該有效。 跳至下一個步驟。

   | 選項 | 說明 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | 輸入執行Elasticsearch或OpenSearch之電腦的完整主機名稱或IP位址。<br>雲端基礎結構上的Adobe Commerce：從您的整合系統中取得此價值。 |
   | **[!UICONTROL Server Port]** | 輸入Web伺服器Proxy連線埠。 預設值為9200<br>雲端基礎結構上的Adobe Commerce：從您的整合系統中取得此價值。 |
   | **[!UICONTROL Index Prefix]** | 輸入搜尋引擎索引前置詞。 如果您對多個Commerce安裝（測試和生產環境）使用單一執行個體，則必須為每次安裝指定唯一的前置詞。 否則，您可以使用預設首碼magento2。 |
   | **[!UICONTROL Enable HTTP Auth]** | 按一下 **[!UICONTROL Yes]** 只有在您已啟用搜尋引擎伺服器的驗證時。 若是如此，請在提供的欄位中提供使用者名稱和密碼。 |
   | **[!UICONTROL Server Timeout]** | 輸入嘗試建立與Elasticsearch或OpenSearch伺服器的連線時等待的時間長度（以秒為單位）。 |

1. 按一下 **[!UICONTROL Test Connection]**.

   範例回應：

   ![成功](../../assets/configuration/elastic_test-success.png)

   繼續使用：

   - [為您的搜尋引擎設定Apache](../../installation/prerequisites/search-engine/configure-apache.md)
   - [為您的搜尋引擎設定nginx](../../installation/prerequisites/search-engine/configure-nginx.md)

   或者您會看到：

   ![失敗](../../assets/configuration/elastic_test-fail.png)

若是如此，請嘗試下列步驟：

- 確定搜尋引擎伺服器執行中。
- 如果伺服器與Commerce位於不同的主機上，請登入Commerce伺服器並Ping搜尋引擎主機。 解決網路連線問題，並再次測試連線。
- 檢查您開始Elasticsearch或OpenSearch的命令視窗，找出棧疊追蹤和例外。 您必須先解決這些問題，才能繼續。 請特別確定您是以使用者的身分啟動搜尋引擎， `root` 許可權。
- 請確定 [UNIX防火牆和SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) 都會停用，或設定規則以讓您的搜尋引擎和商務能夠相互通訊。
- 驗證 **[!UICONTROL Server Hostname]** 欄位。 確定伺服器可供使用。 您可以改為嘗試伺服器的IP位址。
- 使用 `netstat -an | grep <listen-port>` 命令來驗證 **[!UICONTROL Server Port]** 欄位未由另一個處理序使用。

   例如，若要檢視搜尋引擎是否在其預設連線埠上執行，請使用以下命令：

   ```bash
   netstat -an | grep 9200
   ```

   如果它在連線埠9200上執行，則會顯示類似下列的內容：

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## 重新索引目錄搜尋並重新整理整頁快取

變更搜尋引擎組態之後，您必須重新索引目錄搜尋索引，並使用[管理]或[命令列]重新整理整頁快取。

若要使用「管理員」重新整理快取：

1. 在「管理員」中，按一下 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 選取旁邊的核取方塊 **[!UICONTROL Page Cache]**.
1. 從 **[!UICONTROL Actions]** 清單中，按一下 **重新整理**.

   ![快取管理](../../assets/configuration/refresh-cache.png)

使用命令列清除快取： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

使用命令列重新索引：

1. 以或切換為身分登入您的Commerce伺服器， [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 輸入下列任一命令：

   輸入以下命令，只重新索引目錄搜尋索引：

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   輸入下列命令以重新索引所有索引子：

   ```bash
   bin/magento indexer:reindex
   ```

1. 等候重新索引完成。

   >[!INFO]
   >
   >與快取不同，索引器會由cron工作更新。 確定 [cron已啟用](../cli/configure-cron-jobs.md) 開始使用搜尋引擎之前。
