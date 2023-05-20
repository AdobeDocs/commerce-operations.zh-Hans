---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# 代碼片段

## 僅限Commerce {#commerce-only}

>[!NOTE]
>
>此 [!DNL Upgrade Compatibility Tool] 僅適用於Adobe Commerce執行個體。

<!-- Configuration guide snippets -->

## 檔案系統擁有者 {#file-system-owner}

>[!WARNING]
>
>所有MagentoCLI命令都必須由 [檔案系統擁有者](/help/configuration/cli/config-cli.md#prerequisites).

## 備份命令 {#tip-backup-command}

>[!TIP]
>
>此 `support:backup` 命令為 _not_ 執行的相同程式碼備份 `setup:backup` 命令。 此 `support:backup` 命令旨在備份程式碼，以供Adobe Commerce支援人員檢查。

## 僅限Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能僅適用於Adobe Commerce執行個體。

## 已棄用分割資料庫 {#deprecate-split-db}

>[!IMPORTANT]
>
>分割資料庫功能為 [已棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) 在Adobe Commerce 2.4.2版中。 另請參閱 [從分割資料庫還原為單一資料庫](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 與舊版不相容的變更 {#bics}

>[!NOTE]
>
>Adobe Commerce和Magento Open Source版本可能包含與舊版不相容的變更(BIC)。 若要檢閱與回溯不相容的變更，請參閱 [BIC參考](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 主要與回溯不相容的問題說明於 [BIC重點提示](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). 並非所有發行版本都會推出主要BIC。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>從2.3.2版開始，我們將指派並發佈索引式常見漏洞與暴露(CVE)編號，以及外部各方回報給我們的每個安全性錯誤。 這可讓使用者更輕鬆地識別其部署中未解決的漏洞。 若要進一步瞭解CVE識別碼，請前往 [CVE](https://cve.mitre.org/).
