---
title: 此 [!UICONTROL Security] 標籤
description: 瞭解 [!UICONTROL Security] 索引標籤/ [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 此 [!UICONTROL Security] 標籤

此 **[!UICONTROL Security]** 標籤說明安全性問題並隔離其可能原因。 此外，還說明標籤的框架。

## [!UICONTROL API calls by IP, details by URL]

此 **[!UICONTROL API calls by IP, details by URL]** 影格會顯示所選時間範圍內依IP排列的API呼叫數。 此框架會顯示IP位址和該IP位址所存取的API URL。

![依IP的API呼叫](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

此 **[!UICONTROL Forgot Password]** 存取範圍顯示所選時間範圍內忘記密碼的嘗試次數。 針對IP位址的高活動可能是網站上的攻擊。

![忘記密碼](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

此 **[!UICONTROL Create Account access]** 框架顯示所選時間範圍內新帳戶活動的數量。 來自單一IP位址的高活動可能表示有攻擊。

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

此 **[!UICONTROL POST activities]** 框架顯示 `POST` 網站活動，面向 `client_ip` 從 [!DNL Fastly] 記錄。 它也會顯示IP位址存取的URL。

![POST活動](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

此 **[!UICONTROL POST activities summary table]** 框架顯示摘要 `POST` 網站活動，面向 `client_ip` 從 [!DNL Fastly] 記錄。 它也會顯示IP位址所存取URL的計數。 該計數適用於所選的時間範圍。

![POST — 活動 — 摘要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

此 **[!UICONTROL POST activities details table]** 框架顯示 `POST` 網站的活動 [!DNL Fastly] 記錄。 它也會顯示以下連結中的所有詳細資料： [!DNL Fastly] 記錄這些請求。 僅限於最後2000個請求。
![POST — 活動 — 詳細資訊](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

此 **[!UICONTROL Guest Carts activities]** frame會以存取的IP位址和URL為分面，顯示所選時間範圍內的訪客購物車活動數。 客用購物車可能用於梳理攻擊。 此框架顯示存取客體購物車URL的請求總數。

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

此 **[!UICONTROL API – forgot password, create account by Countries]** frame顯示所選時間範圍內已建立的帳戶數以及重設忘記密碼的請求。 它會以多面向顯示請求的原產國。 此框架著重於請求的來源國家/地區。

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

此 **[!UICONTROL API - forgot password, create account by Countries and IP address]** frame顯示所選時間範圍內已建立的帳戶數以及重設忘記密碼的請求。 它會以面向顯示IP位址、存取的URL，以及請求的來源國家/地區。 此框架著重於IP計數。

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

此 **[!UICONTROL Guest cart activities by IP]** 框架會依選定時間範圍內的IP顯示訪客購物車活動。

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

此 **[!UICONTROL Guest cart activities by Countries]** 影格會依國家/地區顯示選定時間範圍內的訪客購物車活動。

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
