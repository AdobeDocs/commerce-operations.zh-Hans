---
title: 發行說明
description: 瞭解Adobe Commerce可用的修補程式及其解決的問題。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 205a0b67fab14a313d28355eed668d60ce477e64
workflow-type: tm+mt
source-wordcount: '12066'
ht-degree: 0%

---

# 發行說明

此 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供Adobe和Magento Open Source社群開發的個別修補程式。 它可讓您套用、還原和檢視已安裝的Adobe Commerce或Magento Open Source版本可用的所有個別修補程式的一般資訊。 無論修補程式的開發者是誰，您都可以將修補程式套用至Adobe Commerce和Magento Open Source專案。 例如，您可以將社群開發的修補程式套用至Adobe Commerce專案。

>[!INFO]
>
>另請參閱 [套用修補程式](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) 以取得將修補程式套用至Adobe Commerce或Magento Open Source專案的指示。 另請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 軟體更新指南中的完整清單，以檢閱已發行的修補程式。

>[!INFO]
>
>如需有關的資訊 [!DNL quality patches] 由社群建立以供Magento Open Source，請參閱 [發行說明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) — 修正Recaptcha v2在提交失敗付款後未重新載入的問題。
* **ACSD-50817** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 最佳化Cron工作 `sales_clean_quotes` 以更快的速度執行。
* **ACSD-49392** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) — 修正套件產品的部分退款後，訂單狀態變更為已關閉的問題。
* **ACSD-51036** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正同時執行REST API呼叫時的競爭條件會覆寫以下檔案中的出貨狀態資訊的問題： [!UICONTROL Items Ordered] 表格。
* **ACSD-50858** (Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 改善載入橫幅內容的效能。
* 已新增MDVA-39305-v2、ACSD-45169的新版本。
* 更新修補程式ACSD-50260-v2。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) — 修正當產品重新補充庫存或價格變更時，未傳送產品警示電子郵件的問題。
* **ACSD-50367** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正建立沒有值的多重選取客戶地址屬性時，客戶地址匯出無法運作的問題。
* **ACSD-49877** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正行動裝置上無法自動播放視訊的問題 [!DNL Safari] 視訊直接連結至遠端視訊檔案，而非串流服務時。
* **ACSD-50165** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正錯誤 *無法刪除檔案。 Warning！unlink：沒有這樣的檔案或目錄* 從Admin排清JS/CSS快取時。
* **ACSD-49737** (適用於Adobe Commerce和Magento Open Source >=2.4.1-p1 &lt;2.4.7) — 修正卡片付款失敗後，優惠券被錯誤地標籤為使用的問題。
* **ACSD-50814** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正管理員使用者無法建立銷退折讓單的問題。
* **ACSD-50116** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正管理員使用者無法為子類別層級3或更低層級建立URL重寫的問題。
* **ACSD-49513** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5) — 修正遠端儲存體同步作業因0位元組檔案而失敗的問題。
* **ACSD-46683** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正運費顯示的問題 *尚未計算*.
* **ACSD-49129** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正 *[!UICONTROL content]* 屬性（base64影像代碼）未傳回 `rest/V1/products/sku/media` 產品媒體API回應。
* **ACSD-50276** (適用於Adobe Commerce >=2.4.0 &lt;2.4.7) — 修正建立多選客戶屬性時，店面無法顯示客戶登錄檔單的問題。
* **ACSD-50527** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正儲存具有空白動態區塊的頁面時發生的錯誤。
* **ACSD-49973** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 改善透過GraphQL擷取套件產品的效能。
* **ACSD-51114** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正啟用非同步索引時，大型目錄中隨機產品消失的問題。 改善大型目錄的非同步重新索引效能。
* **B2B-2598** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 將快取功能新增至 [!UICONTROL availableStores]， [!UICONTROL countries]， [!UICONTROL country]， [!UICONTROL currency]、和 [!UICONTROL storeConfig] GraphQL查詢。
* 已新增MDVA-42806、ACSD-48627、ACSD-46815的新版本。
* 更新ACSD-49773、ACSD-47179、ACSD-48300的修補程式中繼資料。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正訂單未準備好取貨時，API傳送準備好取貨電子郵件的問題。
* **ACSD-49822** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正 [!UICONTROL Requisition List] 頁面未反映在 [!UICONTROL Print Requisition List].
* **ACSD-48771** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正從舊版升級欄區塊內容型別的問題 [!DNL Page Builder] 版本。
* **ACSD-49464** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正當orderId不同時，商業發票、出貨及銷退折讓單不會從封存移回的問題。
* **ACSD-49773** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正使用AWS S3作為遠端儲存時，產品匯出失敗的問題。
* **ACSD-49748** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正無法傳送邀請的問題。
* **ACSD-49502** (適用於Adobe Commerce >=2.4.3 &lt;2.4.7) — 修正將中繼更新套用至可下載產品後，可下載連結未正確更新的問題。
* **ACSD-49527** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正GraphQL公司角色未正確顯示分頁的問題。
* **ACSD-49706** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正未選取任何值時為視覺色票屬性儲存預設值的問題。
* **ACSD-49835** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正使用預設核取方塊值未正確儲存於多選屬性的存放區層級的問題。
* **ACSD-49898** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正當套件產品的特殊價格超過1000時，產品格線擲回例外狀況的問題。
* **ACSD-50234** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.5) — 修正以下訂單時確認電子郵件中客戶名稱有誤的問題： [!DNL PayPal].
* **ACSD-49960** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正客戶訂單格線無法依日期篩選的問題。
* **ACSD-49849** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正客戶電子郵件被取代的問題 [!DNL PayPal] 使用以下方式下訂單時傳送電子郵件： [!DNL PayPal Express] 透過GraphQL。
* **ACSD-49839** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正當產品在SKU中有單引號或雙引號時，共用目錄定價和結構會在「管理員」中擲回錯誤的問題。
* **ACSD-49970** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正下列情況下對GraphQL錯誤的不正確處理： [!DNL New Relic] 報告功能已開啟。
* **ACSD-50260** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正GraphQL產品搜尋結果限製為僅限10,000個結果的問題。
* **ACSD-48813** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正搜尋未根據屬性的搜尋權重顯示相關結果的問題。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.3) — 修正根據「是/否」屬性建立的型錄價格規則未考量所選範圍的問題。
* **ACSD-47704** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正隨附產品僅顯示現成產品價格的問題。
* **ACSD-49370** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正 *日期時間* 產品屬性具有 *FilterMatchTypeInput* 輸入GraphQL結構描述。
* **ACSD-48807** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.7) — 修正透過GraphQL斯托雷克未篩選客戶產品評論的問題。
* **ACSD-49433** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正未結金額的禮品卡購物車中，預設金額顯示為小計的問題。
* **ACSD-48866** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正請求類別的RSS摘要時會發生錯誤的問題。
* **ACSD-48784** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正客戶群組之間不正確快取客戶區段價格的問題。
* **ACSD-48857** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正使用者在使用頁面產生器編輯後無法儲存變更的問題。
* **ACSD-49065** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正僅指派給自訂庫存時，管理員中看不到報價專案的問題。
* **ACSD-49179** (對於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正當不同商店有不同貨幣時，訂單報表顯示不正確金額的問題。
* **ACSD-49286** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正當頁面上存在多個產品Widget時，產品會新增至購物車兩次的問題。
* **ACSD-49574** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 新增功能以透過GraphQL支援購物車中的禮品卡產品更新。
* 更新修補程式：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (適用於Adobe Commerce >=2.4.1 &lt;2.4.7) — 修正使用可轉讓報價下訂單時，使用預設送貨地址而非新送貨地址的問題。
* **ACSD-48059** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正商家無法儲存「」的問題[!UICONTROL Match product by rule]」在類別中。
* **ACSD-48216** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修正以下問題： [!UICONTROL AUTO_INCREMENT] 的 [!UICONTROL inventory_source_item] 表格增加於 [!UICONTROL UPDATE] 作業。
* **ACSD-47908** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修正結帳期間在送貨步驟上選取來源和數量時，出現「值小於或等於0 」的錯誤。
* **ACSD-49497** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正訂單在出貨後仍處於處理狀態且已套用部分退款的問題。
* **ACSD-48694** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) — 修正錯誤「請求的狀態變更無效」導致客戶無法下訂單的問題。
* **ACSD-49013** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正使用大量API建立客戶時，電子郵件確認未轉譯為網站地區設定的問題。
* **ACSD-48164** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正受限管理員無法儲存網站層級值的問題。
* **ACSD-48404** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正按瀏覽器的上一頁按鈕時，「記住類別分頁=是」會導致錯誤的問題。
* **ACSD-48634** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正當發生下列情況時，中繼更新頁面上的JS錯誤：[!UICONTROL Google Analytics Content Experiments]「」已啟用。
* **ACSD-49042** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正無法從店面訂購無限延期交貨的產品的問題。
* 更新修補程式：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (適用於Adobe Commerce和Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) — 修正由於應用程式層級的快取而不一定傳送價格下降通知的問題。
* **ACSD-48661** (對於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正如果公司的信用額度大於999，逗號分隔符號會因為驗證錯誤而阻止儲存公司的問題。
* **ACSD-48773** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正從錯誤商店取得回報點數電子郵件範本的問題。
* **ACSD-48587** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正產品Widget比對規則中HTML特殊字元導致無法顯示相符產品的問題。
* **ACSD-48212** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正產品匯入將產品指派給錯誤來源的問題。
* **ACSD-47988** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正產品匯出從頁面產生器產品說明中裁剪HTML標籤的問題。
* **ACSD-48366** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正貼補庫存電子郵件範本未顯示產品影像的問題。
* **ACSD-48417** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正為產品建立排程變更並儲存另一個產品後出現SQL錯誤的問題。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正未將套件產品指派給任何網站時，產品價格重新索引無法運作的問題。
* **ACSD-48262** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正當「允許每頁所有產品」設定設為「是」時，前端不會顯示產品的問題。
* **ACSD-48293** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4) — 修正已售出的子產品恢復庫存時，複合產品無庫存的問題。
* **ACSD-47520** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正建立銷退折讓單時，客戶會失去獎勵點數的問題。
* **ACSD-48044** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正將多張禮品卡套用至有多張出貨的單一訂單時，無法下訂單的問題。
* **ACSD-48300** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正移除可設定產品時無法建立傳回的問題。
* **ACSD-47910** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正個別實體網格中遺漏訂單、發票、出貨及銷退折讓單的問題。
* **ACSD-47292** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正「顯示無庫存產品」設為「是」時，GraphQL回應中無法使用無庫存套件產品的問題。
* **ACSD-48234** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正啟用「顯示無庫存」選項時，目錄搜尋結果顯示錯誤類別專案計數的問題。
* **ACSD-48313** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5) — 修正屬性值包含逗號時，無法剖析「configurable_variations」欄的問題。 「additional_attributes」使用相同的剖析演演算法。
* **ACSD-48627** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正當傳送GraphQL請求以取得購物車詳細資料時，沒有庫存的可設定產品會導致錯誤的問題。
* 更新修補程式：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正沒有針對具備以下條件的產品產生SEO易記URL的問題： *url_key* 在存放區檢視層級上覆寫的屬性。
* **ACSD-46865** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正啟用非同步索引時，未填入出貨和銷退折讓單格線的問題。
* **ACSD-47004** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正沒有VAT ID的帳單地址未套用VAT的問題。
* **ACSD-47803** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正無庫存可設定產品色票顯示為可用的問題。
* **ACSD-47137** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 當pub/media資料夾非常大時，提升影像庫的載入速度。
* **ACSD-46770** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正傳送管理員訂單電子郵件的問題，即使在 *電子郵件訂單確認* 未勾選。
* **ACSD-47955** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正GraphQL未正確顯示購物車折扣的問題。
* **ACSD-46617** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正 *繼續結帳* 即使小計大於設定的，按鈕也會呈現灰色 *最小訂購金額*.
* **ACSD-47079** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正當子產品庫存狀態透過REST APIPOST/rest/V1/inventory/source-items變更時，複合產品（套件、分組和可設定）庫存狀態未更新的問題。
* **ACSD-47336** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正 *發生錯誤。* 在Commerce Admin中關閉通知時發生錯誤。
* **ACSD-47559** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正「預覽電子郵件範本」區域未完全可見的問題。
* **ACSD-47920** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正透過Rest API以訪客使用者身分下訂單的問題，即使在 *允許訪客結帳* 關閉。
* 已取代的修補程式：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正存取特定範圍受限的管理員無法刪除產品評論的問題。
* **ACSD-47107** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5) — 修正將目錄價格規則折扣套用至自訂產品選項的問題。
* **ACSD-47232** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正無法在管理員中套用具有總權重條件的優惠券的問題。
* **ACSD-46519** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.6) — 修正GraphQL categoryList要求傳回錨點類別不正確product_count的問題。
* **ACSD-47027** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正更新緩慢的CompanyRole GraphQL請求。
* **ACSD-47666** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修正「管理員>系統>許可權>使用者角色>角色>角色使用者」格線中無法運作篩選功能的問題。
* **ACSD-47497** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正「管理」下的「設定」中看不到「服務」索引標籤的問題。
* 更新修補程式：ACSD-47743。
* 已取代的修補程式：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.3) — 修正 _正在嘗試存取型別bool值的陣列位移_ 存取PHP 7.4上已知產品的特定非現有類別路徑時發生錯誤。
* **ACSD-47332** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正cron失敗並只在執行00:00到00:59 UTC之間回報錯誤的問題。
* **ACSD-47280** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正特定範圍上停用共用目錄功能無法正常運作的問題。
* **ACSD-47106** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正無法在公司建立頁面上的新自訂屬性中儲存值的問題。
* 更新修補程式：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正使用者在指派大量產品來源時會發生錯誤的問題。
* **ACSD-46856** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 透過系統>設定>匯入>進階定價，改善效能並更新層級價格。
* **ACSD-46541** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正刪除訂單專案時，管理員使用者無法建立銷退折讓單的問題。
* **ACSD-46581** (對於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正了在購物車中選擇國家/地區後，估計稅金總計未更新的問題。
* **ACSD-46618** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正產品清單Widget針對登入客戶顯示不正確快取價格的問題。
* **ACSD-46674** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正客戶電子郵件中將影像型別的自訂選項顯示為HTML的問題。
* **ACSD-46988** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正GraphQL &#39;currency&#39; API要求傳回自訂貨幣NULL值的問題。
* **ACSD-47076** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5) — 修正無法在店面播放Vimeo影片的問題。
* **ACSD-45071** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4) — 修正匯入期間將預設來源新增至產品的問題。
* **AC-3023** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 將DHL配置更新至最新版本10.0。
* 更新修補程式：MDVA-42584。
* 已取代的修補程式：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5*) — 修正使用者使用商店積分退款時獲得錯誤訂單狀態的問題。
* **ACSD-46703** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6*) — 修正無法在產品編輯頁面上拖放自訂選項的問題。
* **ACSD-44851** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6*) — 修正具有子類別的類別無法開啟或展開的問題。
* **ACSD-46815** (*適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6*) — 修正類別樹狀結構請求限於20個類別的問題。
* **ACSD-45675** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6*) — 修正產品匯出使用來自的類別名稱的問題 *預設存放區檢視* 範圍。
* **ACSD-46869** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6*) — 修正購物車中可設定的產品未透過 *PUTREST API* 請求而不變更產品數量。
* **MDVA-42768-V2** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正可設定產品將正常價格顯示為的問題 *0* 時間 *顯示無庫存* 是 *是*.
* 更新修補程式：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 已棄用的修補程式：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正類別樹狀結構請求限於20個類別的問題。
* **ACSD-45781** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.2*) — 修正行動裝置上未顯示商店前方搜尋欄位的問題。
* **ACSD-46192** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;2.4.5*) — 修正使用的問題 `async/bulk/V1/configurable-products/bySku/options` 端點。
* **ACSD-46404** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5*) — 修正管理員使用者在升級至2.4.4後無法登入的問題。
* 更新修補程式：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正特定存放區的GraphQL產品突變會傳回所有可設定變體的問題，包括未指派給請求存放區的變體。
* **ACSD-46146** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.6*) — 修正管理員下訂單後傳送兩封訂單確認電子郵件的問題。
* **ACSD-45255** (*若為Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修正受限制管理員使用者的「低庫存報告」頁面上的例外狀況。
* **ACSD-45488** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6*) — 修正具有多個來源的可設定產品未自動傳回庫存的問題。
* **ACSD-45754** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.6*) — 修正將優惠券套用至購物車後未新增獎勵點數的問題。
* **ACSD-45849** (*若為Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修正套用中繼更新後視訊中繼資料遺失的問題。
* **ACSD-45257** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.4*) — 修正GraphQL未正確顯示購物車折扣的問題。
* **ACSD-44938** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4*) — 修正以下問題： `VAT_ID` 無法套用至訪客使用者的GraphQL要求。
* 更新修補程式：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.4*) — 修正建立銷退折讓單後虛擬產品庫存數量計算錯誤的問題。
* **ACSD-43887** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正啟用公司的訂購單時，結帳付款頁面上顯示不正確詳細資料的問題。
* **ACSD-45143** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5*) — 修正 `setShippingAddressesOnCart` 變異不允許將數值區域碼設為 *區域*.
* **ACSD-44591** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.6*) — 修正未經CAPTCHA確認而下訂單時發生的錯誤。
* **ACSD-45520** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.6*) — 修正使用者從購物車編輯可設定產品時，未在產品詳細資料頁面上預先選取色票選項的問題。
* **ACSD-45169** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.6*) — 修正以下問題： [!DNL Visual Merchandiser] 套用分段更新後，不會顯示可設定產品的正確庫存和價格。
* **ACSD-45424** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.6*) — 修正部分退款（銷退折讓單）後建立錯誤預訂補償的問題。
* **MDVA-42807** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.6*) — 修正商店正面未顯示自訂貨幣符號的問題。
* 更新修補程式：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正限制管理員使用者的「訂單」報表中訂單總計計算錯誤的問題。
* **MDVA-44940** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正從管理員儲存類別時發生的SQL錯誤。
* **MDVA-44562** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.2-p2*) — 修正無論GraphQL請求源自非預設商店檢視，報價專案的非預設商店ID仍會被預設商店ID覆寫的問題。
* **MDVA-43167** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正管理員使用者選取所有訂單時，管理員訂單格批次動作不適用於多頁的問題。
* **MDVA-44044** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.2-p2*) — 修正將產品指派至新網站後，未顯示在類別頁面上的問題。
* **MDVA-42509** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.4*) — 修正無法快速上傳CSV而導致 *無法傳送Cookie* 錯誤。
* 更新修補程式：MDVA-41061、MDVA-42584。
* 新字首的 [!DNL Quality Patches Tool] 修補程式將變更自 *MDVA* 至 *ACSD* 因為內部程式變更。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正當購物車中已有最小專案數量時，無法將其他專案新增到購物車的問題。
* **MDVA-44887** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5*) — 修正 *未攔截到的SyntaxError：未預期的權杖&#39;const&#39;* 「管理」面板中發生錯誤。
* **MDVA-43718** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正 *使用者無權存取%resources。* 從自訂整合存取共用目錄時顯示的錯誤。
* **MDVA-44660** (*適用於Adobe Commerce和Magento Open Source >=2.4.2-p1 &lt;2.4.5*) — 修正抑音符號字元的問題 ``` ` ``` 無法用於客戶的名字和姓氏。
* **MDVA-40896** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正 *錯誤： TypeError：傳遞給Magento的引數3* 非同步產品大量API時發生錯誤。
* **MDVA-38559** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.3*) — 修正 */V1/customers/search API* 具有多個訂閱的客戶發生錯誤。
* **MDVA-44533** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.4*) — 修正錯誤將折扣套用至套件組合子產品的問題。
* 更新修補程式：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正產品的問題 *無法個別顯示* 仍會出現在目錄進階搜尋結果中。
* **MDVA-44100** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正將所有FPT指派給購物車中最後一個產品並重設其他產品的問題。
* **MDVA-43605** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.5*) — 修正使用Rest API時，訂單資料傳回列總計負值的問題。
* **MDVA-43102** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.5*) — 修正透過REST API完成退款時，可銷售數量未正確更新的問題。
* **MDVA-43178** (*適用於Adobe Commerce和Magento Open Source >=2.4.3-p2 &lt;2.4.5*) — 修正無法在GraphQL中擷取自訂存放區之客戶權杖的問題。
* **MDVA-43859** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正錯誤的問題 *沒有具有customerId =* 當已刪除的客戶嘗試登入時記錄。
* **MDVA-44147** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正GraphQL請求未傳回「請購單清單」的問題。
* **MDVA-44505** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.3*) — 修正GraphQL套用獎勵點數未更新總量，以及在下單期間多次套用商店點數的問題。
* 更新修補程式：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.3*) — 修正當「客戶區段」設定為時，「相關產品規則」才能運作的問題 *全部*.
* **MDVA-39605** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.5*) — 修正Redis快取TTL （到期日）的值錯誤的問題。
* **MDVA-43862** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.5*) — 修正客戶因GraphQL而無法更新購物車專案的問題 *UpdateCartItems突變* 錯誤。
* **MDVA-43824** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 修正以折扣取消訂單時出現錯誤的問題。
* **MDVA-43451** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正錯誤的問題 *找不到要求的存放區。 請驗證存放區，然後再試一次。* 會在為特定網站設定共用目錄時顯示。
* **MDVA-43491** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.5*) — 修正為多商店網站匯入產品時，基本影像標籤未更新的問題。
* **MDVA-43601** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正完整重新索引後觸發器遺失的問題。
* **MDVA-42046** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修正更新產品時，使用日期輸入欄位將錯誤值指派給產品屬性的問題。
* **MDVA-43935** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正向上銷售產品顯示兩次的問題。
* **MDVA-44188** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正系統核發的電子郵件問題，包括 `.-` 中的地址不會傳送。
* **MDVA-42283** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正法語地區設定的管理順序格線中的日期時間格式無效的問題。
* 更新修補程式：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 已新增修補程式的中繼資料 [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.3.6*) — 修正使用者可編輯作用中排程更新開始時間的問題。
* **MDVA-42410** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正優惠券報表僅顯示預設基本貨幣的問題。
* **MDVA-41136** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正「 」的到期日問題 `mage-cache-sessid` 不會擴充，進而導致客戶資料清理。
* **MDVA-39993** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修正透過API完成的詳細目錄變更未反映在前端產品頁面上的問題。
* **MDVA-42855** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正結帳時新客戶地址未儲存至通訊錄的問題。
* **MDVA-42645** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正當商店信用功能停用時，管理員無法退還獎勵點數的問題。
* **MDVA-43414** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) — 修正執行 `inventory.reservations.updateSalabilityStatus` 在數值SKU上將消費者排入佇列。
* **MDVA-41628** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5*) — 修正新增新模組時，現有受限管理員使用者存取新資源的問題。
* **MDVA-43348** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正禮品卡GraphQL請求在下列情況下顯示錯誤的問題 `gift_card_options` contain *uid*.
* **MDVA-39546** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正編輯期間，測試版更新的開始日期可能設定為早於目前日期的問題。
* **MDVA-42950** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正視訊無法在產品頁面上播放的問題。
* **MDVA-42689** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正Adobe Commerce擲回 *完整性條件約束違規* 在匯入期間更新產品類別時發生錯誤。
* **MDVA-41229** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正可設定產品匯入後，前端可用的影像未顯示的問題。
* **MDVA-43731** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正以下問題： *搜尋同義字* 在中新增值時不再運作 *要比對的最少字詞*.
* **MDVA-43232** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.5*) — 修正中排序產品的問題 [!DNL Visual Merchandiser] 依特殊價格至最低/最高會導致儲存類別時發生錯誤。
* **MDVA-43726** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.3*) — 修正部分重新索引後，根據存放區層級屬性比對的目錄價格規則無法套用的問題。
* 更新修補程式：MDVA-36464、MDVA-37478、MDVA-38608。
* 已新增修補程式的中繼資料 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正無法透過REST API更新特定網站的產品價格屬性的問題。
* **MDVA-41350** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正具有受限存取權的管理員使用者依順序將產品新增至其角色範圍以外時，擲回例外狀況的問題。
* **MDVA-42269** (*適用於Adobe Commerce和Magento Open Source >=2.4.3-p1 &lt;2.4.5*) — 修正管理員使用者因 *TypeError： strtotime()預期引數1為字串，指定為null* 錯誤。
* **MDVA-40830** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正下單期間多次套用商店點數的問題。
* **MDVA-42237** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正可設定產品特殊價格在其子產品價格變更後未更新的問題。
* **MDVA-42520** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正以下情況時套用稅率兩次的問題 *啟用跨境貿易* 已使用。
* 更新修補程式：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已棄用的修補程式：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*適用於Adobe Commerce和Magento Open Source >=2.3.2 &lt;2.4.5*) — 修正大量屬性更新只會在變更後為預設存放區建立URL重寫的問題 *產品可見度*.
* **MDVA-43091** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正從後端管理員訂購套件產品時，造成錯誤的問題 *您無法對此產品使用小數數量*.
* **MDVA-40816** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正相關產品規則顯示規則條件中未定義類別之產品的問題。
* **MDVA-41305** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正GraphQL突變新增至願望清單後，未傳回可設定產品選項的問題。
* **MDVA-39181** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正相關產品規則顯示規則條件中未定義類別之產品的問題。
* **MDVA-42584** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正透過「匯入」或API變更數量與庫存狀態後，後端中可設定的庫存狀態未更新的問題。
* **MDVA-40175** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.3*) — 修正以下問題： *按一下以變更送貨方法* 在重新排序期間，不會顯示用來在管理員中選取送貨方法的選項按鈕。
* **MDVA-42768** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.5*) — 修正下列問題：可設定產品在下列情況下，將正常價格顯示為0： *顯示無庫存* 是。
* **MDVA-43201** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正搭配特定地區設定使用DOB屬性時，客戶登入發生錯誤的問題。
* 更新修補程式：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正當Adobe Commerce時區與本機環境時區不同時，日期篩選器無法正常運作的問題。
* **MDVA-42657** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正管理員使用者無法在客戶區段條件中選取類別的問題。
* **MDVA-42806** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正 *新公司註冊* 每次透過REST API更新現有公司時，都會傳送電子郵件。
* **MDVA-37984** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正 [!DNL Visual Merchandiser] *依規則比對產品* 功能無法正確篩選具有中繼更新的產品。
* **MDVA-40488** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正具有無庫存子產品之可設定產品無法顯示在其正確價格範圍的問題。
* **MDVA-42507** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正套用購物車規則的測試版更新後，清除整頁快取的問題。
* **MDVA-39163** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.5*) — 修正當新使用者註冊且購物車中的產品來自訪客工作階段時，無法使用送貨方法的問題。
* **MDVA-38626** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.5*) — 修正管理員使用者無法透過以下路徑在後端下訂單的問題： [!DNL PayPal Payflow Pro] 付款。
* **MDVA-38666** (*適用於Adobe Commerce和Magento Open Source >=2.3.2 &lt;2.3.6*) — 修正管理員使用者無法變更客戶購物車中可設定產品選項的問題。
* **MDVA-38526** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正管理員使用者無法存取 [!DNL Site-Wide Analysis tool].
* 更新修補程式：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正使用者在設定後收到500錯誤的問題。 *影像訊息* Cookie （如果已經存在），但沒有任何新訊息。
* **MDVA-41139** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正當簡單產品的數量=0代表其來源之一時，可設定產品在產品匯入後會變成無存貨的問題。
* **MDVA-42326** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正即使永續性購物車已啟用，客戶在工作階段逾時後結帳時仍發生錯誤的問題。
* **MDVA-42341** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正 `categoryList` 如果請求具有商店標頭，GraphQL查詢不會篩選結果。
* **MDVA-38393** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正重新命名簡單產品時，目錄規則停止對可設定產品運作的問題。
* **MDVA-39153** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正在Admin中重新排序時折扣金額計算錯誤的問題。
* 更新修補程式：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.3*) — 修正管理員使用者在刪除網站後無法存取客戶網格的問題。
* **MDVA-40311** (*適用於Adobe Commerce和Magento Open Source >=2.4.2-p2 &lt;2.4.4*) — 修正管理員使用者收到錯誤訊息的問題 *無效的安全性或表單金鑰。 請重新整理頁面* 登入管理員後（如果已設定自訂管理員路徑且啟用秘密金鑰）。
* **MDVA-41631** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正使用者嘗試在沒有選用專案的情況下擷取訂單資訊時發生錯誤的問題 *電話* 透過GraphQL評估值。
* **MDVA-27239** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.3.6*) — 修正未顯示交叉銷售產品的問題。
* 更新修補程式：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.4*) — 修正重新索引期間前端遺失產品的問題。
* **MDVA-40120** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正依DESC/ASC排序的GraphQL無法搭配具有相同相關性或價格的產品運作的問題。
* **MDVA-41399** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.2*) — 修正管理員使用者無法存取 *管理購物車* 頁面（如果客戶將產品新增至願望清單）。
* **MDVA-40609** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正「 」中缺少已停用產品資料的問題。 `cataloginventory_stock_status` 索引表，顯示不正確的停用產品數量。
* **MDVA-39031** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正可能透過GraphQL將產品新增至購物車的問題，即使未指派至目標網站亦然。
* **MDVA-41597** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正使用者在使用GraphQL將多個可設定產品新增至購物車時出現錯誤的問題。
* **MDVA-27456** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.3.7*) — 修正使用者嘗試載入時發生錯誤 [!DNL Swagger].
* **MDVA-32776** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.2*) — 修正下單但未出貨時庫存狀態未更新的問題。
* **MDVA-30862** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.0*) — 修正列印PDF發票上訂單日期不正確的問題。
* 改善的索引頁面 [!DNL Quality Patch Tool]. 新增方便的搜尋和篩選功能 [!DNL quality patches] 工具的最新版本。
* 更新修補程式：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正先前已移除結束日期時無法建立新的或編輯產品現有排程更新的問題。
* **MDVA-41046** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正具有自訂選項的簡單產品可指派給可設定/分組產品的問題。
* **MDVA-40545** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正即使同一頁面有多個節點，僅擷取頁面的第一個節點的問題。
* **MDVA-41164** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3-p1*) — 修正管理員使用者無法儲存或編輯具有檔案或影像型別自訂客戶屬性的公司的問題。
* **MDVA-39229** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正更新目錄規則中繼更新開始時間後，導致下列錯誤顯示的問題： *Cron工作staging_synchronize_entities_period有錯誤：無法刪除作用中的更新。*
* **MDVA-40619** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正嘗試在CMS頁面上執行內聯編輯時，CMS頁面階層變更會導致500錯誤的問題。
* **MDVA-41061** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正從管理員儲存產品時，庫存狀態重設為可銷售的問題。
* **MDVA-31763** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正目錄價格規則在手動重新索引前還原（或不套用）的問題。
* **MDVA-37748** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正GraphQL查詢傳回未指派給共用目錄之產品的問題。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正無法透過REST API同時建立相同訂單之部分商業發票的問題。
* **MDVA-40101** (*適用於Adobe Commerce和Magento Open Source >=2.3.2 &lt;2.4.0*) — 修正使用成功下訂單後，並未從迷你購物車移除專案的問題 [!DNL PayPal Express] 結帳。
* **MDVA-40401** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正即使下訂單失敗，優惠券使用量值也會變更的問題。
* **MDVA-40537** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) — 修正使用者建立商店檢視時，若存在多個CMS頁面具有相同的URL索引鍵時會發生錯誤的問題。
* **MDVA-37725** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) — 修正從非預設網站傳送的非同步訂單電子郵件包含預設網站的標誌URL的問題。
* **MDVA-39482** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正當啟用延期交貨時，以「0」數量匯入的產品缺貨的問題。
* **MDVA-40435** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.4*) — 修正透過GraphQL套用時，具有動態價格的套件產品折扣不正確的問題。
* **MC-42528** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) — 修正 `categoryList` GraphQL查詢會傳回已指派和未指派的類別。
* **MDVA-29400** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修正以下專案的重複訂單問題： [!DNL PayPal Express Checkout].
* **MDVA-26005** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) — 修正無法在購物車價格規則條件的類別樹狀結構中選取類別的問題。
* **MDVA-25631** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) — 改善編輯和儲存包含大量客戶的客戶區段的效能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正GraphQL搜尋查詢未顯示在Admin熱門搜尋辭彙的問題。
* **MDVA-40601** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) — 修正使用者嘗試取得類別相關資訊時發生錯誤，而該類別已透過GraphQL排程更新變更。
* **MDVA-37234** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修正針對相同SKU將專案多次新增至購物車（平行請求）時，會為相同購物車ID建立重複條列專案的問題。
* **MDVA-33606** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) — 修正使用者取得「 」的問題 *不重複限制違規* 儲存指派給階層的CMS頁面時發生錯誤。
* **MDVA-31590** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) — 修正使用者無法使用MySQL非同步佇列大量更新屬性的問題。
* **MDVA-36309** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修正管理格線中依屬性搜尋產品速度緩慢的問題。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正從商店貸方支付訂單時，具有FPT的商業發票顯示錯誤的總計金額的問題。
* **MDVA-37364** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;=2.4.3*) — 修正日期型別的自訂客戶屬性破壞客戶網格UI的問題。
* **MDVA-39195** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修正以下問題： *加入購物車* 重新導向至購物車已啟用時，類別頁面上的按鈕未啟用。
* **MDVA-37115** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修正不需要的問題 *只剩下0個* 通知會顯示在可設定的產品頁面上。
* **MDVA-39521** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4*) — 修正使用者無法透過GraphQL以空白電話號碼在購物車上設定送貨地址的問題。
* **MDVA-39384** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修正未儲存公司使用者的自訂客戶屬性的問題。
* **MDVA-39043** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.4.3*) — 修正具有有限存取權的管理員使用者嘗試新增 *產品* CMS頁面的Widget。
* **MDVA-39966** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 修正部署錯誤地區設定的問題。
* **MDVA-38852** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) — 修正目錄存貨（依設計）鎖定表格以進行更新，而在同時訂購多筆並行訂單的情況下，大幅降低效能的問題。
* **MDVA-39986** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.3*) — 修正使用者無法使用Safari瀏覽器在MacOS的「管理員」中下訂單的問題。
* **MDVA-38447** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正兩個問題： *無法個別顯示* 可設定的子產品會傳回GraphQL回應，並使用類別篩選器最佳化GraphQL產品查詢的MySQL查詢。
* **MDVA-40134** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正啟用共用目錄時，GraphQL未傳回相關產品的問題。
* **MDVA-39935** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正GraphQL傳回可在網站層級停用的可設定子產品的問題。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4*) — 修正 *呼叫成員函式getId()* 錯誤會顯示在管理員的訂單詳細資訊頁面上。
* **MDVA-34948** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修正長時間執行的查詢的問題，例如 `GET_LOCK`.
* **MDVA-39305** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) — 修正註冊客戶無法以已啟用的Google ReCaptcha登入的問題。
* **MDVA-37897** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正客戶嘗試使用「最近檢視」Widget的選項新增產品時，重新導向不正確的問題。

## v1.1.0 {#v1-1-0}

* 我們引進了修補程式類別，以改善使用者體驗，並讓客戶更輕鬆地搜尋所需的修補程式。
* 此 `patches.json` 檔案已重新命名為 `support-patches.json`.
* **MDVA-38799** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正建立中繼更新後未儲存可下載產品的問題。
* **MDVA-37592** (*適用於Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修正指定至共用目錄之零價格的產品無法正確依價格排序的問題。
* **MDVA-38827** (*若為Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) — 修正客戶收到包含錯誤訊息的訂單出貨電子郵件的問題。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*適用於Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修正儲存CMS頁面時的錯誤： *具有相同ID PAGE_ID的專案已存在*.
* **MDVA-34680** (*若為Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修正客戶格線中無法正確篩選客戶帳戶建立時間的問題。
* **MDVA-37068** (*若為Adobe Commerce >=2.3.1 &lt;2.4.4*) — 修正當購物車只有虛擬產品時顯示錯誤稅率的問題。
* **MDVA-38608** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正重新索引未成功完成時，未刪除暫存資料表的問題。
* **MDVA-38308** (*若為Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) — 修正新增的相關問題 [!DNL Vimeo] 產品影片。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*若為Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修正使用時，客戶未導向「付款確認」頁面的問題。 [!DNL Paypal Payment Advanced] 方法。
* **MDVA-37082** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正儲存分組產品的自訂庫存時導致產品在前端無庫存顯示的問題。
* **MDVA-36572** (*若為Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修正銷退折讓單更新不再導致資料庫重複產品預訂更新的問題。
* **MDVA-38132** (*若為Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修正由於下列原因而無法存取管理員面板的問題： *太多重新導向* 錯誤。
* **MDVA-38270** (*若為Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正GraphQL中訂單總計遺失禮品卡資訊的問題。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*若為Adobe Commerce >=2.4.2 &lt;=2.4.4*) — 修正當網站ID與商店ID不一致時，透過GraphQL將可設定產品新增到購物車的問題。
* **MDVA-36832** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修正當檢視寬度為768px時，影像在頁面上重複的問題。
* **MDVA-37874** (*若為Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 修正以下問題： *整個購物車的固定折扣金額* 錯誤地套用至包含多個選項的套件組合產品。
* **MDVA-37913** (*適用於Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) — 修正透過API更新可下載產品時，可下載連結消失的問題。
* **MDVA-34330** (*適用於Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) — 修正「訂單」格線中的訂單未根據管理員時區進行篩選的問題。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*若為Adobe Commerce >=2.3.0 &lt;=2.3.7*) — 修正Adobe Commerce針對以下訂單建立部分發票時擲回錯誤的問題： *分期付款方式* 透過REST API的付款方法。
* **MDVA-37362** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修正GraphQL回應中，可設定的產品選項值和變數屬性值為空白的問題。
* **MDVA-37288** (*適用於Adobe Commerce 2.4.2*) — 修正GraphQL要求後傳回錯誤層級價格的問題。
* **MDVA-37225** (*若為Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) — 修正當匯入的SKU中有整數值時，快速建立訂單期間上傳流程卡住的問題。
* **MDVA-37224** (*適用於Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) — 修正客戶無法支付可協商報價的問題 [!DNL PayFlow Pro] 與購物車中的其他產品整合。
* **MDVA-36286** (*適用於Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修正若同一SKU在子類別中具有不同位置，頁面產生器產品Widget預覽會中斷的問題。
* **MDVA-30186** (*若為Adobe Commerce >=2.3.4 &lt;=2.3.5-p2， >=2.4.0 &lt;=2.4.0-p1， >=2.4.2 &lt;=2.4.2-p1*) — 修正GraphQL回應中，屬性選項是依選項值而非屬性專案計數排序的問題。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*若為Adobe Commerce >=2.3.0 &lt;=2.4.2*) — 修正透過API變更舊自訂選項後仍保留的問題。
* **MDVA-35773** (*若為Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) — 修正具有100%折扣之訂單的商業發票上，總金額未顯示為零的問題。
* **MDVA-36833** (*適用於Adobe Commerce 2.4.2*) — 修正搜尋結果在從共用目錄排除某些產品後，每頁顯示隨機產品數的問題。
* **MDVA-37182** (*若為Adobe Commerce >=2.4.1 &lt;=2.4.2*) — 修正兩者中取得錯誤搜尋結果的問題 [!DNL Elasticsearch] 第6版和第7版。
* **MDVA-36253** (*適用於Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) — 修正刪除專案後，迷你購物車中顯示錯誤小計的問題。
* **MDVA-36853** (*適用於Adobe Commerce 2.4.2*) — 修正載入大型媒體集時影像未顯示的問題。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修正類別頁面上遺失套件式產品的問題。
* **MDVA-36615** (*適用於Adobe Commerce 2.4.2*) — 修正管理員產品格線中產品計數不正確的問題。
* **MDVA-36464** (*若為Adobe Commerce >=2.4.0 &lt;=2.4.2*) — 修正電子郵件通知設定無法在存放區檢視層級運作的問題。
* **MDVA-36138** (*適用於Adobe Commerce ^2.3.2*) — 修正送貨價格未調整的問題，且購物車中並非所有專案都符合免運費購物車規則時，會向客戶顯示完整送貨價格。
* **MDVA-36424** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — 修正當後端基底URL與店面基底URL不同時，內容重複編輯時，附加至頁面產生器元素的媒體影像消失的問題。
* **MDVA-35984** (*適用於Adobe Commerce ^2.4.0*) — 修正建立相同產品的多個並行出貨後，產品數量與可銷售數量不正確的問題。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*若為Adobe Commerce >=2.3.4 &lt;2.4.2*) — 這修正了GraphQL查詢未使用類別快取標籤快取的問題。
* **MDVA-33168** (*若為Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正透過API更新產品屬性時，所有其他屬性會變更為空值的問題。
* **MDVA-19640** (*適用於Adobe Commerce >=2.3.0*) — 修正以下問題： [!DNL Advanced Reporting] 未顯示任何資料。
* **MDVA-11189** (*若為Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正匯入CSV檔案以更新產品庫存後，來自的列的問題 `cataloginventory_stock` 表格即被刪除。
* **MDVA-26639** (*若為Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) — 修正建立新訂單確認電子郵件範本時，訂單郵件中遺失訂單專案的問題。
* **MDVA-15546** (*適用於Adobe Commerce >=2.3.0*) — 修正建立訂單後 *資料行entity_id where子句模稜兩可* 錯誤會顯示在例外狀況記錄檔中。
* **MDVA-21095** (*若為Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正查詢時的問題 `INSERT INTO search_tmp` 不會於整批屬性值更新後結束。
* **MDVA-23845** (*若為Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修正啟用JavaScript縮制後無法預覽電子郵件範本的問題。
* **MDVA-22026** (*若為Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正從CSV檔案（包括來自外部URL的影像）匯入產品時失敗的問題。
* **MDVA-22383** (*若為Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正儲存產品需要很長時間且分頁的問題。
* **MC-41359** (*若為Adobe Commerce >=2.3.6-p1 &lt;2.3.7， >=2.4.2 &lt;2.4.3*) — 修正SameSite Cookie引數設定不正確的問題。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*適用於Adobe Commerce 2.4.1*) — 修正Page Builder擲回以下錯誤的問題： *起始頁面產生器時發生錯誤。 請洽詢您的技術支援連絡人。*
* **MDVA-35356** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正取消已部份開立商業發票的訂單後，不正確的商店退款問題。
* **MDVA-33289** (*若為Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修正下列情況，在簽出期間，帳單地址UI中顯示原始JavaScript程式碼的問題 [!DNL Google Tag Manager] 已啟用。
* **MDVA-35982** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正管理員使用者受限於特定網站時，無法為同一網站上的訂單建立運送的問題。
* **MDVA-35155** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正選項標題變更時無法購買套件組合產品的問題。
* **MDVA-35910** (*若為Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正停用「以客戶身分登入」功能後無法建立新客戶帳戶的問題。
* **MDVA-34474** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正使用API將產品新增至請購單清單的問題。
* **MDVA-34591** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正的購物車規則折扣計算不正確的問題。 *最大數量折扣套用至* 和 *折扣數量步驟（購買X）*.
* **MDVA-33704** (*若為Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修正 *店內取貨* 雖然已將送貨選項設定為可用，但並未顯示。
* **MDVA-34928** (*若為Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修正從付款中移除商店點數後，頁面載入器會無限期顯示的問題。
* **MDVA-35254** (*若為Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正簽出時驗證碼的問題。
* **MDVA-35569** (*若為Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正 *固定產品稅金* 指定狀態時，GraphQL回應中未填入欄位。
* **MDVA-35847** (*若為Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正使用自訂客戶屬性時公司使用者表單中斷的B2B問題。
* **MDVA-31307** (*若為Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正的問題 *記憶體不足* 由於快取區塊的動態CSP白名單發生問題，導致某些類別發生錯誤。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正錯誤 *進行中* 訊息狀態為正確 *complete* 給消費者的訊息 `quoteItemCleaner` 刪除數個產品後。
* **MDVA-34102** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正「產品格線」和「編輯產品」頁面上「管理」區域中已停用產品的預設庫存量為零。
* **MDVA-35286** (*若為Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正客戶將產品捆綁在購物車中，並從多個地址簽出切換為線上簽出的錯誤問題。
* **MDVA-35312** (*若為Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) — 修正空白GraphQL請求時的回應代碼500。
* **MDVA-34189** (*若為Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修正503第一個位元組逾時於 [!DNL Visual Merchandiser] 載入管理員類別頁面時的查詢。
* **MDVA-34695** (*若為Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正負面 `children_count` 刪除類別之後。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*若為Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正 *使用預設值* 套用排定的變更後，核取方塊就會清除。 排程的變更一旦不再有效，問題就會出現。
* **MDVA-35064** (*若為Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修正無法針對透過API建立的可設定產品產生URL重寫的問題。
* **MDVA-34943** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正快速訂購快取先前輸入的SKU的問題。
* **MDVA-35197** (*若為Adobe Commerce >=2.3.5 &lt;2.4.0*) — 修正先前新增的產品無庫存時，使用GraphQL新增購物車時出現錯誤的問題。
* **MDVA-34850** (*若為Adobe Commerce >=2.3.1 &lt;2.4.0*) — 修正未顯示可供設定產品的無庫存選項，而非顯示為刪除字元的問題。
* **MDVA-34867** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正排程更新的條件欄位集值未儲存的問題。
* **MDVA-35092** (*若為Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修正使用者無法新增的問題 [!DNL Vimeo] 因已棄用的影片 [!DNL Vimeo] API。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*若為Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修正如果相符產品對每個網站的價格不同，頁面產生器產品內容型別預覽會中斷的問題。
* **MDVA-32634** (*適用於Adobe Commerce ^2.3.1*) — 修正 `url_path` 在階層中移動類別後，指派給所有商店的類別維持不變。
* **MDVA-33344** (*適用於Adobe Commerce ^2.3.0*) — 修正硬式編碼的問題 `rma_item` 會使用實體預設屬性集ID，而非資料庫中的值。
* **MDVA-34192** (*若為Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修正無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。
* **MDVA-34847** (*適用於Adobe Commerce ^2.3.0*) — 修正具有自訂許可權之管理員使用者的管理員集合中，針對SQL條件，儲存ID型別轉換為整數的問題。
* **MDVA-34886** (*適用於Adobe Commerce ^2.3.2*) — 修正搜尋未傳回結果的問題，如果 *權重* 產品屬性已設定為可搜尋。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正的問題 [!DNL PayPal Payflow Pro] 付款失敗，並出現重新導向引數清單格式錯誤。
* **MDVA-34023** (*若為Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正錯誤的問題 *沒有addressId的實體* 會在訪客的瀏覽器上隨機顯示。
* **MDVA-32759** (*若為Adobe Commerce >=2.3.1 &lt;2.4.3 （含B2B擴充功能）*) — 修正共用目錄刪除現有層定價的問題。
* **MDVA-33482** (*適用於Adobe Commerce ^2.3.5*) — 修正針對部份商業發票產生「銷退折讓單」時，導致訂單總額的稅捐，而非該部份商業發票的稅捐的問題。
* **MDVA-33393** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正錯誤 *提供的國家/地區識別碼不存在*.
* **MDVA-33632** (*若為Adobe Commerce >=2.3.0 &lt;2.3.7*) — 提供例外狀況訊息的修正 *此產品無庫存* 嘗試重新訂購無庫存產品時，現在會向管理員使用者顯示。
* **MDVA-34469** (*若為Adobe Commerce >=2.4.1 &lt;2.4.2*) — 修正使用多個商店檢視時，客戶購物車上的GraphQL突變失敗的問題。
* **MDVA-33976** (*若為Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修正從套件產品移除第二個選項後，在店面將套件產品顯示為無存貨的問題。
* **MDVA-33894** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1 （含B2B擴充功能）*) — 修正快速訂購功能的多個問題，包括新增和移除多個產品以及SKU區分大小寫。
* **MDVA-27664** (*若為Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正客戶登錄檔單中顯示錯誤的問題： *錯誤 — 出生日期不應晚於今天。*
* **MDVA-33970** (*若為Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正當價格屬性的範圍設定為網站時，銷退折讓單中出現錯誤貨幣符號的問題。
* **MDVA-33992** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正B2B特殊定價在結帳時顯示不正確的問題。
* **MDVA-34100** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2 （含B2B擴充功能）*) — 修正無法從公司結構頁面建立公司帳戶的問題。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*若為Adobe Commerce >=2.3.3 &lt;2.3.5， >=2.4.0 &lt;2.4.2*) — 修正從CSV檔案匯入產品後，影像重複的問題。
* **MDVA-33382** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正從類別中移除產品後索引器失效的問題。
* **MDVA-28511** (*若為Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修正無法完成的問題 [!DNL PayPal] 如果「名稱」欄位包含特定字元（如重音大寫字母），請結帳。
* **MDVA-31519** (*若為Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修正使用全網站銷售規則時，訪客結帳的等待逾時問題。
* **MDVA-33281** (*若為Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正中發生嚴重錯誤的問題。 `inventory:reservation:list-inconsistencies` 因為SKU引數型別錯誤。
* **MDVA-24201** (*若為Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正價格在手動重新索引之前無法反映排程購物車價格規則的問題。
* **MDVA-32694** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修正管理員使用者無法新增產品至可議價報價的問題（若產品與非預設商店有關）。
* **MDVA-33516** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正編輯請購單清單中的套件組合產品會導致錯誤的問題。
* **MDVA-33975** (*若為Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正GraphQL要求中與價格計算相關的多個問題。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正的問題 [!DNL PayPal] 結算報告不可用於 **報表** > **銷售** > **[!DNL PayPal]** 如預期結算。
* **MCP-87** (*若為Adobe Commerce >=2.3.1 &lt;2.4.2*) — 改善大型設定檔的類別產品和庫存索引器的索引時間。
* **MDVA-33106** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正重新排程的產品變更在cron後遭到清除的問題 `run` 命令會執行。
* **MDVA-19391** (*若為Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正以下問題： `analytics_collect_data` 由於NULL描述記錄在 `catalog_category_entity_text` 表格。
* **MDVA-20376** (*若為Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正的問題 *沒有具有customerId = 1的此類實體* 中的錯誤 `exception.log` 適用於下單後登入的客戶。
* **MDVA-23764** (*若為Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正中的錯誤 `JsFooterPlugin.php` 這會影響動態區塊的顯示。
* **MDVA-13203** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正 *完整性條件約束search_tmp_表格* 完全重新索引後會出現錯誤。
* **MDVA-23426** (*若為Adobe Commerce >=2.3.3 &lt;2.3.5*) — 修正Adobe Commerce傳送的通知電子郵件含有空白內文，且內容已新增為附件的問題。
* **MDVA-22150** (*若為Adobe Commerce >=2.3.1 &lt;2.3.4*) — 修正在Admin中停用可設定產品後，在購物車中具有可設定產品且已套用優惠券的客戶無法登入的問題。
* **MDVA-32545** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正從管理員建立訂單時，未自動寄出發票的問題。
* **MDVA-32714** (*若為Adobe Commerce >=2.3.4 &lt;2.4.1*) — 修正客戶群組價格在GraphQL產品查詢中無法運作的問題。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*若為Adobe Commerce >=2.3.2 &lt;2.4.2*) — 新增 *小計(包括 Tax)* 訂價規則條件的選項。
* **MDVA-31236** (*若為Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正具有自訂資源存取權的管理員無法設定2FA或登入的問題。
* **MDVA-30845** (*若為Adobe Commerce >=2.3.5 &lt;2.3.7*) — 修正 *抱歉，目前此訂單沒有報價* 無法連線到UPS XML/USPS/DHL時會顯示錯誤，且沒有其他送貨方法可用。
* **MDVA-32133** (*若為Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正某些情況下媒體集未從頁面產生器載入的問題。
* **MDVA-12304** (*適用於Adobe Commerce >=2.3.0*) — 將Cookie的最大數量從50增加到200。
* **MDVA-32632** (*若為Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正訂單出現在付款系統，但未出現在Adobe Commerce中的問題。
* **MDVA-32449** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 （含B2B擴充功能）*) — 修正訂單歷史記錄載入非常緩慢或完全沒有載入的問題。
* **MDVA-32739** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正啟用非同步電子郵件通知傳送舊銷售電子郵件的問題。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*適用於Adobe Commerce 2.3.6、2.4.1*) — 修正 *建立帳戶* 修正「 」中的無效資料後，按鈕保持停用狀態。 *建立新的客戶帳戶* 表單。
* **MDVA-31006** (*適用於Adobe Commerce 2.3.0、2.3.1*) — 修正使用下訂單後出現重複訂單的問題 [!DNL Paypal Express] 付款。
* **MDVA-25602** (*適用於Adobe Commerce 2.3.0*) — 修正的問題 [!DNL PayPal Payflow Pro] 付款方式及將Cookie視為 `SameSite=Lax` 預設情況下，在Chrome 80瀏覽器和API回應中重新導向至客戶登入頁面。

## v1.0.10 {#v1-0-10}

修補程式版本的微幅修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*若為Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修正具有抵用券的購物車價格規則未透過GraphQL套用的問題。 *整個購物車的固定金額折扣* 動作已使用。
* **MDVA-30889** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正以虛擬和簡單產品作為選項開立套件組合發票後發生錯誤的問題。
* **MDVA-31791** (*若為Adobe Commerce >=2.3.4 &lt;2.3.5*) — 改善使用目標規則或連結產品時的產品頁面效能。
* **MDVA-31168** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正產品匯出CSV檔案未出現，以及記憶體配置錯誤的問題。
* **MDVA-32313** (*若為Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正可能使用錯誤的設定選項將可設定產品新增至願望清單的問題。
* **MDVA-31759** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正產品未更新的問題 *下拉式清單* 和 *文字區域* CSV匯入期間的屬性值。
* **MDVA-32012** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正韓國和阿根廷的郵遞區號無法驗證的問題。
* **MDVA-31640** (*若為Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 修正無法透過REST API更新特殊價格的問題。
* **MDVA-28651** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 （含B2B擴充功能）*) — 修正透過REST API載入可轉讓報價時發生效能問題的問題。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1 （含B2B擴充功能）*) — 修正「銷退折讓單」網格中顯示錯誤貨幣符號的問題。
* **MDVA-31295** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正部分訂單完成且專案徵稅時，未計算獎勵點數的問題。
* **MDVA-30112** (*若為Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正訂購數量超過 *束團大小* 值，Adobe Commerce會考量以下專案的訂單： *擱置中* 狀態為不一致。
* **MDVA-31150** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正GETInvoice Rest API呼叫未傳回商店信用與禮品卡餘額的問題，當商業發票以Rest API呼叫過帳，且訂單部分由商店信用與禮品卡帳戶支付時。
* **MDVA-30963** (*若為Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修正產品篩選結果設為僅包含指定值的問題 *所有商店檢視* 在「管理員」中的範圍，包括值在商店檢視層級上覆寫的產品。
* **MDVA-29954** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2含B2B擴充功能*) — 修正 *新的公司註冊要求* 和 *您已連結至公司* 電子郵件是從錯誤的地址傳送。
* **MDVA-28357** (*若為Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 在「 」的SKU欄位中，以具有關鍵字Tokenizer的自訂分析器取代標準分析器 [!DNL ElasticSearch] 索引，讓萬用字元搜尋查詢可搭配包含連字型大小(「 — 」)的SKU運作。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正自訂訂單狀態變更為的問題 *處理中* 使用WebApi建立部分出貨後。
* **MDVA-30428** (*若為Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修正客戶無法將產品新增至願望清單的問題（若此產品已指派至自訂詳細目錄來源）。
* **MDVA-30594** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正設定FPT時，簽出期間無法儲存多個位址的訂單的問題。
* **MDVA-29148** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正透過API呼叫（的產品自訂屬性）建立產品時的問題。 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如Multiselect）如果承載中未提供值，則型別不會使用其預設值。
* **MDVA-30837** (*若為Adobe Commerce >=2.3.1 &lt;2.3.5*) — 新增組態設定 *包含稅捐至金額：是/否* 「免運費」方法設定中的。 時間 *包含稅捐至金額* 設為 *是*，最小訂購金額的計算方式為小計+稅捐。 時間 *包含稅捐至金額* 設為 *否*，最小訂購金額以小計計算
* **MDVA-25028** (*若為Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) — 修正以下方式下訂單時的問題： [!DNL PayPal Payflow Pro] 觸發欺詐篩選時，未設定為疑似欺詐狀態。
* **MDVA-31224** (*若為Adobe Commerce >=2.3.3 &lt;2.3.5*) — 改善的效能 `catalog_product_price` 為套件產品重新編列索引作業。
* **MDVA-31321** (*若為Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正以下情況時的空白頁面（錯誤）： *全部顯示* 「 」已選取。 [!DNL Elasticsearch] 會傳回產品id的大型清單。 在此案例中，order by子句會轉換為不正確的SQL格式。
* **MDVA-30815** (*若為Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正當您變更搜尋結果頁面上應顯示多少搜尋結果時，Adobe Commerce會顯示空白頁面的問題。 [!DNL Elasticsearch] 現在當您變更每頁檢視的搜尋結果數目時，可以正確顯示類別頁面的結果。
* **MDVA-30782** (*若為Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修正無論購物車規則為何，都會顯示動態區塊的問題。
* **MDVA-31021** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正中的效能問題 `module-catalog-import-export/Model/Import/Product/Option.php`. 如果中有超過~100k筆記錄 `catalog_product_option` 表格，含有單一產品的新CSV需要不到10秒的時間進行驗證。
* **MDVA-31007** (*若為Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正自訂地址屬性未正確顯示在我的帳戶區域和後端的訂單詳細資訊頁面中的問題。
* **MDVA-29389** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正進階報告的問題，其中 `analytics_collect_data` cronjob說： *連線埠必須在主機引數中設定（例如localhost：3306）*.
* **MDVA-31343** (*若為Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正移除body類別的問題 `page-layout-category-full-width` 類別已排程時。
* **MDVA-30945** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正更新購物車時收到嚴重錯誤訊息的問題 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*若為Adobe Commerce >=2.3.4 &lt;2.4.0*) — 實作 *最小值應符合* 功能和部分搜尋 [!DNL Elasticsearch] 引擎。 解決搜尋查詢中連字型大小的問題。
* **MDVA-30102** (*若為Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修正Redis快取快速成長的問題，因為版面快取沒有TTL。
* **MDVA-30599** (*若為Adobe Commerce >=2.3.4 &lt;=2.4.0*) — 修正使用API建立的訪客報價錯誤地標示為已登入客戶的報價的問題。
* **MDVA-29446** (*若為Adobe Commerce >=2.3.3 &lt;=2.4.0*) — 修正簽出期間，不適用送貨方法的價格顯示為零的問題。
* **MDVA-30357** (*若為Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修正cron產生Sitemap時，建立錯誤影像URL的問題。
* **MDVA-30565** (*適用於Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) — 修正以下問題： *沒有cartid = 0的實體* 如果啟用了持續購物車，則在店面結帳時會顯示訪客客戶的錯誤。
* **MDVA-29787** (*適用於Adobe Commerce >=2.3.0 &lt;=2.4.0*) — 修正相關產品的目標規則在下列情況下無法運作的問題： *為其中之一* condition用於定義要顯示的產品。
* **MDVA-30977** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) — 修正重新索引後，類別中隨機缺少產品的問題。
* **MDVA-28202** (*若為Adobe Commerce >=2.3.4 &lt;=2.4.2*) — 修正使用MSI時，分層導覽無法正確篩選可設定產品的問題。
* **MDVA-28300** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正GQL請求未反映目錄價格規則價格變更的問題。
* **MDVA-31006** (*若為Adobe Commerce >=2.3.2 &lt;=2.4.2*) — 修正使用下訂單後出現重複訂單的問題 [!DNL Paypal Express] 付款。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*若為Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正分層導覽的問題，其中， *否* 在以下情況下，布林值型別產品屬性的值不會包含在分層導覽中： [!DNL Elasticsearch] 用作搜尋引擎。
* **MDVA-28191** (*若為Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正透過Admin建立訂單期間未載入任何付款方法的問題。
* **MDVA-29959** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 （含B2B擴充功能）*) — 修正受限管理員使用者使用的問題 *公司* 不允許許可權刪除公司帳戶。
* **MDVA-30265** (*若為Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正建立商業發票後，出貨追蹤連結停止運作的問題。
* **MDVA-28409** (*若為Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正 `sales_clean_quotes` cron工作失敗於 *記憶體不足* 當資料庫中過期的引號數量巨大時發生錯誤。
* **MDVA-30593** (*若為Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正未清除根據「報價期限」設定過期的報價的問題。
* **MDVA-30107** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正將不同基底URL用於存放區檢視時，存放區切換器無法正常運作的問題。
* **MDVA-28763** (*若為Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正使用REST API更新產品資訊多次後，產品影像重複的問題。
* **MDVA-30284** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正目錄搜尋索引器因下列原因而失敗的問題 *[!DNL Elasticsearch]錯誤：已超過索引中欄位總數的限制。*
* **MDVA-29042** (*適用於Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 （含B2B擴充功能）*) — 修正目錄許可權變更為的問題。 *允許* 將新產品新增至共用目錄後會自動更新。
* **MDVA-30428** (*若為Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正客戶無法將產品新增至願望清單的問題（若此產品已指派至自訂詳細目錄來源）。
* **MDVA-28661** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2 （含B2B擴充功能）*) — 修正變更公司管理員後， 「公司使用者」公司帳戶區段中擲回錯誤的問題。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*適用於Adobe Commerce 2.3.1 - 2.3.4-p2*) — 修正cron作業在資料庫名稱太長時失敗，導致前端未更新類別的問題。
* **MDVA-30106** (*適用於Adobe Commerce ^2.3.0*) — 修正結帳期間付款未載入的問題 *無法讀取null的屬性&#39;length&#39;* JS主控台發生錯誤。
* **MDVA-28656** (*若為Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) — 修正下列問題：若下訂單時不需要付款資訊（例如，有100%折扣），且已針對訂單建立商業發票，則訂單狀態會變更為 *已關閉* 而非「完成」。
* **MDVA-30209** (*適用於Adobe Commerce 2.3.0 - 2.3.3-p1*) — 修正客戶更新其帳戶資訊時，客戶群組變更為預設的問題。
* **MDVA-30123** (*若為Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正GraphQL查詢的屬性選項標籤未正確轉譯的問題。
* **MDVA-29996** (*若為Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正啟用類別許可權後，完整頁面快取不會快取類別頁面的問題。
* **MDVA-30164** (*若為Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修正存在自訂客戶屬性時無法從客戶格線匯出客戶記錄的問題。
* **MDVA-30444** (*若為Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正使用GraphQL下訂單時不會傳送確認電子郵件的問題。
* **MDVA-30490** (*適用於Adobe Commerce 2.3.4 - 2.3.5-p2*) — 修正產品比較中若有一個產品的簡短描述空白，會擲回500錯誤頁面的問題。
* **MDVA-30232** (*若為Adobe Commerce >=2.3.1 &lt;2.4.1*) — 修正原始訂單含有禮品卡時無法重新訂購的問題。
* **MDVA-29965** (*若為Adobe Commerce >=2.3.3 &lt;2.4.0*) — 修正客戶新增產品至購物車時，收到「無效表單金鑰」錯誤的問題。
* **MDVA-30008** (*若為Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正無法透過管理程式API對公開目錄中的產品下訂單的B2B問題。
* **MDVA-22469** (*適用於Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) — 修正升級至Adobe Commerce 2.3.3後，頁面產生器在「管理」面板中無法運作，以及部分JS和CSS檔案無法載入的問題。
* **MC-35984** (*若為Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正商家為退貨授權(RMA)建立運送標籤後，無法與退貨頁面上的任何頁面元素互動的問題。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*適用於Adobe Commerce 2.3.0 - 2.3.4*) — 修正的問題 [!DNL PayPal Payflow Pro] 付款方式及將Cookie視為 `SameSite=Lax` 預設情況下，在Chrome 80瀏覽器和API回應中重新導向至客戶登入頁面。
* **MDVA-26694** (*若為Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) — 修正產品和目錄快取每天過期的問題，但過期時間排程不同。
* **MDVA-27825** (*若為Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正因記憶體洩漏而導致匯出大量資料失敗的問題。
* **MDVA-29085** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) — 修正B2B問題，若公司是由API建立，則不會傳送必要的新公司電子郵件。
* **MDVA-29344** (*適用於Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) — 修正頁面產生器從標題元素複製文字至文字元素後卡住的問題。
* **MDVA-29835** (*適用於Adobe Commerce >2.3.1 &lt;2.4.2*) — 修正禮品卡訂單包含兩個代碼（而非一個）的問題。
* **MDVA-30052** (*若為Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修正私密內容（本機儲存）未正確填入、導致效能問題的問題。
* **MDVA-30131** (*若為Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正分層導覽的問題，其中， *否* 在以下情況下，布林值型別產品屬性的值不會包含在分層導覽中： [!DNL Elasticsearch] 用作搜尋引擎。
* **MDVA-35514** (*若為Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正在「建立封裝」強制回應視窗中建立出貨標籤及將訂購產品新增至封裝的問題。
