---
title: 預防並回應安全性事件
description: 瞭解避免和回應雲端基礎結構專案中Adobe Commerce安全性事件的最佳做法。
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# 協助預防及回應安全性事件的最佳實務

Adobe Commerce安全性在下 [共擔責任](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 模型。 瞭解Adobe和您的技術團隊的職責至關重要。 以下為摘要 [安全性最佳實務](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) 以確保您的專案具備最佳安全性控制項，以及如何對安全性事件作出最佳回應。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce

## 回應事件

當您回應安全性事件時，有許多考量事項。 如果您懷疑在雲端基礎結構專案中遇到Adobe Commerce最近的安全事件，請務必稽核所有管理員使用者帳戶存取權、啟用進階多重驗證(MFA)控制、保留重要記錄，以及檢閱您Adobe Commerce版本的安全升級。

更多建議詳見下文。 它們有助於防止未經授權的存取，並啟動進一步事件分析的程式。

## 如何防止安全性事件

遵循這些安全性最佳實務，主動預防影響Adobe Commerce網站和店面的安全性事件：

- [啟用2FA以取得管理員存取權](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
雙因素驗證被廣泛使用，通常會在相同應用程式上產生不同網站的存取代碼。 這可確保只有您可以登入使用者帳戶。 如果您遺失密碼或機器人猜到密碼，則雙因素驗證會增加一層保護。
- [為SSH存取啟用MFA](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
在專案上啟用MFA時，雲端基礎結構上所有具有SSH存取權的Adobe Commerce帳戶都必須遵循驗證工作流程，該工作流程需要雙重驗證(2FA)代碼，或API權杖和SSH憑證才能存取環境。
- 升級至最新版Adobe Commerce。
Adobe會針對每個支援的Adobe Commerce發行安全性與功能修補程式。
- 設定和使用 [非預設管理員URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe建議您使用唯一的自訂管理員URL，而非預設值 `admin` 或常用辭彙，例如 *後端*. 雖然此設定變更不會直接保護您的網站免受已判定的不良執行者的傷害，但可減少嘗試獲得未經授權存取的指令碼暴露。
- 防止在Admin中使用編輯或更新設定值  [`bin/magento config:set` 具有的CLI命令 `lock env` 設定選項](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). 此選項會鎖定組態值，使其無法在Admin中編輯，或防止變更已鎖定的設定。 使用此選項時，組態變更會寫入 `<Commerce base dir>/app/etc/env.php` 檔案。
- 設定並執行 [Adobe Commerce安全性掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html).
增強式安全性掃描可讓您監視每個Adobe Commerce網站(包括PWA)，以找出已知的安全性風險和惡意程式，並接收修補程式更新和安全通知。
- [檢閱和更新管理員使用者存取權](https://docs.magento.com/user-guide/system/permissions-users-all.html) 和 [安全性設定](https://docs.magento.com/user-guide/stores/security-admin.html).
   - 建議移除任何舊的、未使用的或可疑的帳戶，並輪換所有管理員使用者的密碼。
   - 檢閱並更新專案的「進階安全性設定」&lt;。 Admin安全性設定可讓您將秘密金鑰新增至URL、要求密碼須區分大小寫，以及限制管理員工作階段的長度，包括密碼的存留期，以及在Admin使用者帳戶鎖定前可以嘗試登入的次數。 為了提高安全性，您可以設定目前工作階段過期前鍵盤閒置的長度，並要求使用者名稱和密碼區分大小寫。
- 稽核Adobe Commerce於 [雲端專案使用者](https://devdocs.magento.com/cloud/project/user-admin.html).
建議移除任何舊的、未使用的或可疑的帳戶，並要求使用者變更密碼。
- 稽核 [ssh金鑰](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) 適用於Adobe Commerce的雲端基礎結構。
我們建議檢閱、刪除和輪換SSH金鑰。
- 對管理員實作存取控制清單(ACL)。
您可以將Fastly Edge ACL清單與自訂結合使用 [VCL程式碼片段](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) 篩選傳入的請求，並允許管理員依IP位址進行存取。

## 分析事件

事件分析的第一步是儘可能快速地收集儘可能多的事實。 收集事件相關資訊可協助您判斷事件的可能原因。 Adobe Commerce提供下列工具，協助您進行事件分析。

- [稽核管理員動作記錄](https://docs.magento.com/user-guide/system/action-log-report.html).
「動作記錄報表」會顯示所有已啟用記錄功能的管理員動作的詳細記錄。 每個記錄都加蓋時間戳記，並註冊使用者的IP位址和名稱。 記錄檔詳細資料包括管理員使用者資料，以及在動作期間所做的相關變更。
- 使用分析事件 [Adobe Commerce工具的觀察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Adobe Commerce觀察工具可讓您分析複雜的問題，以協助找出根本原因。 與其追蹤不同的資料，您可以將時間花在關聯事件和錯誤上，以更深入地瞭解效能瓶頸的原因。
此工具旨在讓您清楚瞭解部分潛在的網站問題，協助您找出根本原因，並讓網站維持最佳效能。 按一下上方Adobe Commerce觀察工具檔案的連結，存取工具檔案。 檔案中有一節詳細介紹可在以下網址找到的所有資訊： **安全性** 標籤。
- 分析記錄檔，使用 [New Relic記錄](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). 雲端基礎結構上的Adobe Commerce Pro專案包括 [New Relic記錄](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) 服務。 此服務已預先設定為彙總中繼和生產環境的所有記錄資料，以便在集中式記錄管理儀表板中顯示。
您可以使用New Relic記錄檔服務來完成下列工作：
   - 使用 [New Relic查詢](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) 以搜尋彙總記錄檔資料。
   - 透過New Relic記錄檔應用程式以視覺效果呈現記錄檔資料。

## 其他資訊

- [根本原因分析框架](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
