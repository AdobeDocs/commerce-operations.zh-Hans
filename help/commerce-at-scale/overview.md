---
title: 大規模提供體驗
description: 瞭解如何使用Adobe Commerce和Adobe Experience Manager大規模提供體驗。
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 使用Adobe Commerce、Commerce Integration Framework和Adobe Experience Manager大規模提供體驗

使用CIF作為聯結器的AEM和Adobe Commerce之間建議的整合模式，是讓AEM擁有展示層（「玻璃」）和Adobe Commerce，將商業後端作為「無頭」後端提供支援。 此整合方法可運用每個應用程式的優勢：AEM的編寫、個人化和全通路功能，以及Adobe Commerce的電子商務營運。

在AEM/CIF/Adobe Commerce環境中，電子商務網站訪客將首先到達AEM。 AEM將檢查其Dispatcher快取中是否有請求的頁面可用。 如果頁面存在，則會將此快取頁面提供給訪客，不需要進一步處理。 如果Dispatcher不包含請求的頁面或頁面已過期，則Dispatcher會請求AEM發佈者建立頁面，發佈者會呼叫Adobe Commerce以取得電子商務資料，並視需要建立頁面。 接著會將內建頁面傳遞給Dispatcher以提供給訪客，然後會快取，以防止其他訪客後續對相同頁面提出請求時，將進一步的載入置於伺服器上。

![AdobeExperience Manager和Adobe Commerce架構概觀圖表](../assets/commerce-at-scale/overview.png)

伺服器端轉譯和使用者端轉譯的組合可用於AEM/CIF/Adobe Commerce模型：伺服器端轉譯可提供靜態內容，而使用者端轉譯則透過從使用者瀏覽器內直接呼叫特定元件的Adobe Commerce，提供經常變更或個人動態內容。

以下範例顯示AEM電子商務店面範例中，產品詳細資訊頁面中不同元件的範例：

![AdobeExperience Manager和Adobe Commerce架構概觀圖表](../assets/commerce-at-scale/product-details-page.svg)

## 伺服器端轉譯

產品詳細資料頁面(PDP)和產品清單頁面(PLP)等電子商務頁面不太可能經常變更，且適合在使用AEM CIF核心元件呈現在伺服器端後完全快取。 頁面應使用在AEM中建立的通用範本在AEM Publisher上呈現。 這些元件會透過GraphQL API從Adobe Commerce取得資料。 這些頁面會以動態方式建立、在伺服器上呈現、在AEM Dispatcher上快取，然後傳送至瀏覽器。 以上範例中的紫色方塊中顯示了這方面的範例。

## 使用者端轉譯

在顯示較動態屬性（例如庫存水準/可用性或價格）的地方(例如在產品詳細資料頁面(PDP))，可以使用使用者端元件。 雖然範本頁面可在Dispatcher上使用上述伺服器端轉譯方法建置和快取，但在靜態頁面本身中可以有動態使用者端Web元件。 這些動態元件可透過GraphQL API，在使用者端的瀏覽器中直接從Adobe Commerce擷取資料，以即時檢查PDP上的目前價格或庫存量。 這可確保在頁面載入時，一律會擷取通常對於即時顯示而言很重要的內容。 以上範例中的紅色方塊中顯示了這方面的範例。

結帳程式期間也可以使用AEM範本和使用者端轉譯的組合：使用者端購物車元件轉譯購物車、結帳表單以及與支付服務提供者的整合。 此混合方法也可用於Adobe Commerce的帳戶管理功能，例如建立帳戶、登入帳戶和忘記密碼。
