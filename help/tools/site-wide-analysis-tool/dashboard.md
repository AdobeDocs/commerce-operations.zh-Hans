---
title: '[!DNL Dashboard]'
description: 瞭解 [!DNL Dashboard] 索引標籤中的 [!DNL Site-Wide Analysis Tool]、元素、使用時間、好處和最佳實務。
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

此 [!UICONTROL Dashboard] 頁面顯示總覽 [!DNL widgets] 提供Adobe Commerce網站運作狀態與目前狀態的「單一窗格檢視」。 每個 [!DNL widget] 內含每個功能頁面的存取連結、每個工具本身或報表(取決於 [!DNL widget])。
此外還有以下清單 [!UICONTROL External Resources] Adobe Commerce的連結，包括 [Adobe Commerce說明中心支援知識庫（說明中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)， [Adobe Commerce開發人員檔案(DevDocs)](https://developer.adobe.com/commerce/docs/)， [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}， [安全中心](https://helpx.adobe.com/security.html)、和 [Adobe Commerce (OAC)的觀察結果](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## 元素

* **[!UICONTROL Recommendations]**：顯示網站的最佳實務建議。 Recommendations （發現的問題和要修正的建議）會依優先順序排序 — P0 （嚴重）到P4 （通知）。
Recommendations包含說明、建議、網站影響、根本原因、案例/先決條件，以及使用的工具。

* **[!UICONTROL Upgrade Compatibility Tool]**：透過分析安裝在Adobe Commerce自訂執行個體中的所有模組和核心程式碼，針對特定版本檢查該執行個體。 它會傳回在升級至最新版Adobe Commerce之前必須解決的關鍵問題、錯誤和警告清單。 它也會識別在嘗試升級至較新版本的Adobe Commerce之前，必須在程式碼中修正的潛在問題。
此 [!UICONTROL Upgrade Compatibility Tool] 可讓您識別自訂功能何時變更核心程式碼。

* **[!UICONTROL Security Center Widget]**：顯示網站的安全性深入分析。
顯示的安全性資訊包括 [技術 [!DNL Stack] 版本法規遵循 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 安全性最佳實務Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
此 [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) 監控Adobe Commerce網站的安全性風險。 它可以主動且有效率地偵測商家商店上的惡意軟體，並在出現任何安全性風險、惡意軟體或威脅時通知商家，還可以識別遺失的Adobe Commerce修補程式和更新。

* **[!UICONTROL Extensions]**：顯示目前安裝在您的Adobe Commerce執行個體上的擴充功能。 [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) 若有可用的擴充功能，亦會提供相關資訊。

* **[!UICONTROL Alerts]**：顯示最新的 [!DNL New Relic Managed Alerts] 適用於Adobe Commerce執行個體。 進一步瞭解 [Adobe Commerce的管理式警報](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) 以及如何 [存取New Relic服務](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) (位於Adobe Commerce支援知識庫)。

* **[!UICONTROL Non-recommended software in use]**：根據您的Adobe Commerce版本，顯示您的Adobe Commerce執行個體目前使用的非建議軟體。 不建議使用的軟體清單為 [!UICONTROL Name]， [!UICONTROL Installed Version]、和 [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**：根據您可能已安裝之修補程式和Adobe Commerce版本，顯示任何建議修補程式的簡短清單。 建議修補程式的完整清單可在 **[!UICONTROL Patches]** 功能標籤，此標籤也位於 [!DNL Site-Wide Analysis Tool]. 修補程式由 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 列出的所有修補程式都與您目前的Adobe Commerce執行個體相容。
如果沒有建議為您的Adobe Commerce執行個體顯示的修補程式，此 [!DNL widget] 將會顯示， **[!UICONTROL No Recommended Patches]**.

## 使用時機

此 **[!UICONTROL Dashboard]** 頁面是您在 [!DNL Site-Wide Analysis Tool] 不僅可輕鬆檢視您網站整體健康情況的「整體狀況」，您還可以透過各個頁面檢視和存取Adobe Commerce網站的特定工具、建議和報告 [!DNL widget].

## 優點

* 此 [!DNL widgets] 的 [!UICONTROL Security Center]， [!UICONTROL Recommendations]， [!UICONTROL Extensions]、和 [!UICONTROL Security Scan] 所有圖表都使用易於閱讀的以顏色編碼的互動式圓形圖表，圖表旁有圖例，中央有計數總計，表示有多少個 [!UICONTROL Recommendations]， [!UICONTROL Extensions]、和 [!UICONTROL Security Scan Tool] 每個功能都有的專案。 [!UICONTROL Recommendations] 和 [!UICONTROL Security Scan Tool] 圖表會依嚴重程度分隔。 [!UICONTROL Extensions] 分為四個分類：目前版本、舊版本、已停用和未知。

* [!DNL New Relic Alerts] 列在最上面，且包含最新警報的簡短說明，以及警報發生的時間。

* 此 [!UICONTROL Recommendations] 和 [!UICONTROL Extensions] [!DNL widgets] 按一下「 」，即可存取每個功能的完整資料頁面 **[!UICONTROL View All]**.

* 此 [!UICONTROL Security Scan Tool] 具有 **[!UICONTROL View Report]** 中的連結 [!DNL widget] 視窗將您帶至 [!UICONTROL Recommendations] 頁面。

* 此 [!DNL Upgrade Compatibility Tool] 具有 **[!UICONTROL Run Upgrade Scan]** 中的按鈕 [!DNL widget] 視窗。

## 使用的最佳實務 [!UICONTROL Dashboard]

* 按一下每個 [!DNL widget] 存取其提供的詳細資料，以深入瞭解並瞭解您網站的安全性、健康狀況、建議及最佳作法來加以改善。

* 前往 [!UICONTROL Security Scan Tool] [!DNL widget] 並按一下 [!UICONTROL View Report] 若要檢視 [!UICONTROL Recommendations] 您網站的報告。

* 使用 [!DNL External Resources] 連結以瞭解詳細資訊、瞭解最新的安全性修補程式、更新和最佳實務，或利用 [Adobe Commerce說明中心支援知識庫（說明中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)， [Adobe Commerce開發人員檔案(DevDocs)](https://developer.adobe.com/commerce/docs/)， [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}， [安全中心](https://helpx.adobe.com/security.html)、和 [Adobe Commerce (OAC)的觀察結果](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
