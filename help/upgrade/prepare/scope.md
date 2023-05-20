---
title: 瞭解升級範圍
description: 瞭解版本中回溯不相容的變更，這些變更可能會影響Adobe Commerce或Magento Open Source自訂模組或協力廠商擴充功能。
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 0%

---

# 瞭解升級範圍

檢閱 [發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) 瞭解版本的範圍，包括增強功能、錯誤修正，以及可能影響協力廠商和自訂模組的已知問題。

## 與舊版不相容的變更

Adobe Commerce和Magento Open Source版本可能包含與回溯不相容的變更。 檢閱我們與舊版不相容的變更檔案，請參閱下列內容：

- **[主要變更重點](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** — 有重大影響並需要詳細說明和特殊說明的變更，以確保協力廠商模組繼續運作。
- **[微幅變更參考](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** — 參考從程式碼庫產生的檔案，說明對類別、API成員資格、資料庫、相依性插入、介面、配置、系統和XSD的次要變更。

## 協力廠商擴充功能

Adobe Commerce Marketplace的新相容性政策可確保 _全部_ 列出的擴充功能與GA發行日起30天內的最新發行版本相容。 因此，請務必儘可能透過Marketplace取得協力廠商擴充功能。

## 自訂模組

所有自訂模組都應針對您想要升級的目標版本進行檢查。 這是最耗用時間和資源的升級程式。 評估自訂模組時，您必須尋找與回溯不相容的變更，並注意新的實務，例如控制器分解。 如需詳細資訊，請參閱 [發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). 此外，請確定您確實遵循 [最佳實務](https://developer.adobe.com/commerce/php/best-practices/extensions/) 用於模組開發。

## [!DNL Upgrade Compatibility Tool]

此 [!DNL Upgrade Compatibility Tool] 是一個命令列工具，可分析您的執行個體是否有潛在的升級問題。 它會檢查您所安裝的目前版本與嘗試升級至的版本之間是否有問題。

使用此工具可減少團隊瞭解升級範圍和影響所需的工作量。 它可協助您在升級時避免常見程式碼問題，並提供如何解決已識別問題的明確方向。 它還有助於優先處理最關鍵的問題，以確保升級成功，在升級時節省時間和成本。

請參閱下列章節，以開始使用 [!DNL Upgrade Compatibility Tool]. 請參閱 [!DNL Upgrade Compatibility Tool] [指南](../upgrade-compatibility-tool/overview.md) 以取得更多技術細節和進階使用案例。

### 下載工具

使用Composer下載工具。 它需要PHP 7.3或更新版本、至少2GB的RAM、Node.js (如果您正在檢查GraphQL相容性)，以及Adobe Commerce授權。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### 執行工具

若要分析您的執行個體並檢查錯誤、警告和嚴重問題：

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> 此 `<dir>` 引數是儲存程式碼基底的目錄。 此 `-c` 選項會將您的程式碼基底與指定版本進行比較。

找出團隊要處理的最重要問題：

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

可搭配此命令使用的其他選項包括：

- `--ignore-current-version-compatibility-issues` — 隱藏目前版本的所有已知嚴重問題、錯誤和警告。 它只會針對您嘗試升級的版本提供錯誤。

- `--min-issue-level` — 可讓您設定最低問題層級，協助只優先處理升級時最重要的問題。 選項包括警告、錯誤和嚴重性遞增順序的嚴重性。

- `-m | [=MODULE-PATH]` — 如果您只想分析某個廠商、模組或甚至目錄，您也可以將路徑指定為選項。

- `--vanilla-dir` — 可讓您檢查核心程式碼，瞭解功能或自訂的任何非標準實作。 請務必事先清除這些專案。 系統會自動下載您版本的vanilla例項以供參考。

   >[!NOTE]
   >
   > 這也可以透過以下方式完成 `core:code:changes` （命令中）。

### 分析輸出

此 [!DNL Upgrade Compatibility Tool] 匯出JSON檔案，識別受影響的程式碼或模組、嚴重性，以及所遇到的每個問題的說明。 它也會輸出具有複雜性分數的摘要報告，讓您的團隊大致瞭解升級至最新版本需要什麼。 複雜性分數越低，執行升級就越容易。

以下輸出顯示範例摘要報告：

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### 提示與建議

報告中會列出工具識別的所有問題，並附上特定錯誤代碼。 使用 [錯誤訊息參考](../upgrade-compatibility-tool/error-messages.md) 以取得每個問題的詳細資訊。 Adobe也提供修正每個問題型別的建議，以便您規劃補救步驟。

使用報告可估計更新您的程式碼以進行升級所需的精力。 根據您的經驗，您可以根據已識別的問題總數和問題的嚴重性來估計升級所需的工作。 由於這是命令列工具，您可以將其併入自動化測試和程式碼檢查套裝，並使用JSON輸出來產生報表。

我們建議您儲存每個升級專案的結果，以便您可以將未來的升級結果與先前的結果進行比較。 透過持續使用，您將會透過工具提供的摘要報告，開始深入瞭解升級至下一個版本所需的精力。

我們也建議您在處理升級工作時定期執行此工具，以便檢視您的進度。 當您修正問題時，問題數量應該會減少。 這也有助於您的團隊決定分發工作的最佳方式。

此 [!DNL Upgrade Compatibility Tool] 將繼續改進，未來版本將包含自動修正等功能，以幫助您儘快修正問題。 2022年1月發佈的最新改進包括PHP 8.1相容性測試和HTML視覺化功能，可幫助您快速識別可能需要更多升級工作的區域。
