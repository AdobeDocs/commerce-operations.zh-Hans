---
title: 發行原則
description: 瞭解不同型別的Adobe Commerce版本，包括次要、修補程式、安全性修補程式、功能、Hotfix、個別修補程式和自訂修補程式。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Adobe Commerce發行原則

Adobe Commerce和Magento Open Source使用 [語意版本設定](https://semver.org/) 在個別模組層級(例如 `magento/framework 101.1.1`)，但不適用於行銷版本號碼。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH版本**—2.4.5
   - **安全性修補程式發行版本**—2.4.5-p1
      - 安全性錯誤修正
      - 安全性增強功能
- **BETA修補程式版本**—2.4.7-beta1
- **功能發行**
- **Hotfix**
- **個別修補程式**
- **自訂修補程式**

## 次要版本

以下准則適用於次要版本：

- 可進行重大變更；針對Adobe Commerce 2.2.x撰寫的程式碼可能無法再搭配Adobe Commerce 2.3.x使用。例如，次要發行版本可能會引入對主要系統需求和相依性的支援，例如PHP。
- 模組版本可能有所不同。 例如，新修補程式中會引入一些模組變更，而次要發行版本中則會引入其他模組變更。
- 次要發行版本可能包括新功能，在升級期間您可能需要或您的解決方案合作夥伴進行額外的工作，以確保相容性。
- 次要發行版本可能包括安全性和品質問題的修正。

## PATCH版本

修補程式發行主要著重於提供安全性、效能、法規遵循以及高優先順序的品質修正，協助您維持網站在尖峰時的效能。

下列准則適用於修補程式發行版本：

- 最新支援的次要版本會收到完整功能品質修正和增強功能。
- 避免進行可能破壞擴充功能或程式碼相容性的變更。 例如，針對2.2.0版撰寫的程式碼仍應適用於2.2.7版。
- 在例外情況下，可能會發行重大變更或額外的修補程式或Hotfix，以解決安全性或法規遵循問題以及高影響力的品質問題。 在模組層級，這些變更主要是PATCH層級的變更；有時是「次要」層級的變更。

### 安全性修補程式發行版本

**安全性錯誤修正**：解決已識別的安全性問題並在受影響的產品區域提供預期結果的軟體程式碼變更。 這些修正通常可回溯相容。

**安全性增強功能**：軟體改進或設定變更，以主動改善應用程式內的安全性。 這些安全性增強功能有助於解決安全性風險，這些風險會影響Adobe Commerce應用程式的安全性狀態，但可能回溯不相容。

使用安全性修補程式發行版本，您無需套用完整修補程式發行版本中包含的其他品質修正和增強功能，即可確保網站更加安全。 安全性修補程式發行版本會附加&#39;-pN&#39;，其中N是從1開始的增量修補程式版本（例如2.3.5-p1）。 安全性修補程式發行版本也可包含解決影響Adobe Commerce應用程式的重大問題所需的Hotfix。

每個安全性修補程式版本都是以之前的完整修補程式版本為基礎。 此版本包含先前修補程式版本的品質和安全修正，以及先前完整修補程式版本和安全修補程式版本之間建立的安全性修正。

如需下載和套用安全性修補程式的說明，請參閱 [快速開始安裝](../installation/composer.md#example---security-patch).

## BETA修補程式版本

Adobe Commerce功能正式發行前的版本已開放所有Adobe Commerce客戶和Adobe合作夥伴使用。 它可讓您在「一般可用性」之前有額外時間檢閱程式碼和受影響的元件。

Beta版可能包含瑕疵，並依「現況」提供，不提供任何型別的保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式) Beta版。 建議客戶謹慎使用，切勿依賴Beta版及/或任何隨附檔案或資料的正確運作或效能。 因此，客戶自行承擔使用測試版的風險。

## 功能發行

功能發行包含新功能和功能更新，這些功能和更新以獨立服務的形式提供，與修補程式發行版本分開。 範例包括產品Recommendations和Live Search等服務、PWA Studio和Inventory management (MSI)等獨立模組，以及雲端服務和基礎結構的更新。

## Hotfix

Hotfix是包含高影響力安全性或品質修正的修補程式，例如影響許多商家的零日漏洞修正。 Adobe Commerce版本的Adobe發行hotfix，目前仍受關鍵安全性或品質問題所支援和影響（視需要）。 Hotfix會發佈至 [已知問題區段](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 我們的知識庫。 這些修正包含在下一個計畫的修補程式發行版本中。

>[!NOTE]
>
>Hotfix可能包含回溯不相容的變更。

## 個別修補程式

個別修補程式包含特定問題的低影響品質修正。 這些修正已套用至支援的Adobe Commerce次要版本。 AdobeAdobe Commerce會視需要，根據 [軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>個別修補程式不包含回溯不相容的變更。

## 自訂修補程式

由非Adobe人員建立，用於修正問題或因各種原因修改Adobe Commerce程式碼。 自訂修補程式會透過 [品質修補工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## 相關主題

- [版本設定](https://developer.adobe.com/commerce/php/development/versioning/)
- [即將發行的版本](schedule.md)
- [軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
