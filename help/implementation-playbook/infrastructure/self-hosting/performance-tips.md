---
title: 自行託管Adobe Commerce效能秘訣
description: 瞭解自行託管效能秘訣，以及可考慮的概念和最佳實務。
landing-page-description: 瞭解自行託管Adobe Commerce時的一些效能秘訣概念和考量事項。
short-description: 瞭解自行託管Adobe Commerce的策略和效能提示概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# 自行託管Adobe Commerce效能秘訣

使用彈性且功能強大的電子商務平台，並不意味著您必須犧牲效能。 自Adobe Commerce成立以來，核心應用程式已獲得許多改善。 在2.5.4版中，Adobe Commerce工程團隊執行了設定測試，以對應用程式進行效能評定。 測試結果證明Adobe Commerce有能力處理超過2.4億個SKU的大型目錄，API請求時間平均為300毫秒，且每小時處理的頁面檢視次數和訂單數令人驚歎，達到了200萬次頁面檢視和208,000次訂單。

前往檢視最新的效能標竿結果 [Experience League- Adobe Commerce — 實作行動手冊 — 效能標竿](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

若要讓一切儘可能保持最佳狀態，請在為專案新增自訂專案和其他複雜性時，請遵循這些標準。

以下小節涵蓋如何最佳化自行託管實作時應考量的主題和建議。

## 清漆

清漆是具有快取的HTTP反向Proxy。 雖然看起來很複雜，但結果會產生快速回應，以協助確保傳回請求的速度比從來源擷取專案快。 在沒有某些版本Varnish的情況下執行Adobe Commerce網站將會導致頁面載入速度和其他關鍵量度變慢。 油漆可能很難自行設定和管理，不過我們在Experience League中也有這個主題 [設定清漆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} 以更進一步瞭解其搭配Adobe Commerce使用的情形。 另一種選擇是使用雲端型解決方案。 雖然考慮的因素很多，但最終還是選擇了Fastly作為Adobe Commerce雲端服務的解決方案。 它是雲端型Fastly的版本，使用VCL和許多清漆。

尋找最適合您的應用程式、設定、預算和技術能力的解決方案，是一項困難的工作。 使用雲端式選項，可讓所有硬體零件消失，直到管理、組態、伺服器和其他基礎架構元件都受到考量。 由於其效能、擴充性、輸送量和許多其他關鍵量度，Adobe Commerce雲端團隊將其選為其解決方案。

透過為您的專案選擇有關Varnish的良好解決方案，您就能為客戶設定最佳效能，並節省商務應用程式的工作量。

## CDN

除了Varnish對您的Adobe Commerce專案來說是一項寶貴的資產外，下一個順理成章的將是CDN。 除了您的Varnish之外，CDN還可以為CSS、頁面資產（例如影像）提供快取例項，以協助減少進入Adobe Commerce應用程式的頻寬。 它可以快取GraphQL回應，進一步發揮Headless Adobe Commerce網站的優點。 有些CDN提供影像最佳化、Web應用程式防火牆和其他功能。

Adobe Commerce on cloud選擇使用Fastly做為其Varnish快取，但也作為其CDN。 此單一解決方案提供多種功能，可為Adobe Commerce雲端客戶提供絕佳體驗。 您可以閱讀Fastly服務的Experience League概觀 [Fastly服務概述](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN可為Adobe Commerce專案提供最佳化且安全的傳送內容。 雖然這可能不是專案的必要元件，但應視為您的網站日趨成熟且訪客數量增加。 藉由提供CDN，您可以延遲新增其他硬體至基礎建設，或因每個要求移除的負載而擴充現有基礎建設。

## 停用模組

應該考慮停用未使用的模組，但不要輕易進行。 此技術的確會為某些要求減少一些開銷和處理時間，但有一些副作用需要考量。 開發人員有時會在建立功能時假設模組可用。 這通常是安全的，除非他們選擇使用某些類別，這些類別可在已停用的模組中找到。

停用模組（例如原生「電子報」）是相當常見的事件。 當商店擁有管理其電子報的第三方公司時，情況尤其如此。 這可能是個問題的情況，即當安裝協力廠商模組時，出於某種原因，他們決定使用電子報中的類別。 在某些初始安裝和測試期間，可能會發現這種意外相依性，但之後您必須決定是否要保留此協力廠商模組、啟用Newsletter，然後回歸測試網站，尋找引入的任何怪異行為。 或者，您是否找到替代該協力廠商模組的專案。 這兩個決定都伴隨著風險、時間以及可能的錯誤。

在停用未使用的模組之前，請確定您沒有任何測試，例如單元、 [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 負載測試或可能受影響的API請求。

## 要求每個提取請求都必須遵循Adobe Commerce和PHP編碼標準

Adobe Commerce有一組 [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. 這些有助於確保遵循類似的模式、樣式和預期設計，無論軟體開發型別為何。 貢獻至Adobe Commerce程式碼基底時，這是必要條件。 但是，如果您選擇遵循此自訂開發方法，可為所有開發人員（包括目前和未來）奠定堅實的基礎。 要求所有提取請求都必須通過程式碼標準時，可確保每個人都能瞭解並期待相同的一致開發模式。

為了配合Adobe Commerce編碼標準，使用的另一個基礎是PHP基本編碼標準。 開發人員指南應清楚定義您須遵循的標準，以及可接受的任何偏差。 不過，後援應參照公開維護的指南，網址為 [PHP-FIG](https://www.php-fig.org){target="_blank"}.

對遵循PSR-1和PSR-12的堅定立場。 確保為專案貢獻內容的開發人員會遵循這些原則，這有助於確保沒有奇怪的結構化檔案和模式。 這也有助於確保未來的開發人員能快速閱讀並瞭解他們所檢閱的程式碼。 您越是遵循這些模式和程式碼標準，表示未來的開發工作應該會更容易閱讀，並更快實作。

## 在每次部署後執行負載測試

在每次部署後執行負載測試可能顯得過度。 但是，如果遵循此方法，則可以追蹤和緩解新推出功能導致效能降低的機會。

除了偵測新程式碼造成效能降低外，擁有您網站關鍵量度的歷史參考，有助於深入瞭解何時啟用新工具或變更基礎架構。 例如，在付費給託管公司以增加您的環境規模並希望您能獲得您期望的效能提升之前，您可以使用新設定設定設定中繼環境，並執行負載測試以檢視實際結果。

這些測試可以自動化，並且是CI/CD管道的一部分。 因此，您也可以建立規則來取得結果，如果偏離標準太多，則可能會阻止特徵合併。 此資料的使用案例數量是無限的，但若不啟動此程式，您可能無法實現其潛力。

Adobe Commerce在Experience League中對此主題有良好的記錄 [效能測試秘訣](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
