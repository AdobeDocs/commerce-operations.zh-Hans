---
title: 內容安全性原則概觀
description: 瞭解如何使用內容安全性原則改善Adobe Commerce或Magento Open Source存放區的安全性狀態。
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# 內容安全性原則概觀

內容安全性原則(CSP)可協助偵測及緩解跨網站指令碼(XSS)和相關資料插入攻擊，為Adobe Commerce和Magento Open Source安裝提供額外防禦層。 這種常見的攻擊向量是透過插入惡意內容來運作，這些內容會錯誤地聲稱源自網站。 惡意內容載入並執行後，可能會起始未經授權的資料傳輸。

CSP提供了一組標準化的指令，用於告知瀏覽器哪些內容資源可以信任，哪些應該封鎖。 使用謹慎定義的原則，CSP可以限制瀏覽器內容，以只允許列入白名單的資源顯示。

## 設定

為避免干擾網站作業，CSP可分階段實施。 CSP有兩種基本操作模式： `report-only mode` 和 `restrict mode`. Adobe Commerce 2.3.5的發行標誌著我們實作的第一個階段，並讓CSP可在 `report-only mode` 依預設。 在未來版本中， `restrict mode` 預設會啟用，以提供額外的現成保護功能。

**僅限報表模式**：指示瀏覽器報告原則違規，但不會強制執行這些違規。 每次請求的資源違反CSP時，瀏覽器都會將產生的錯誤記錄到主控台。 然後可以使用主控台記錄來調查每個違規的原因。

務必在所有CSP錯誤發生時加以檢閱，並調整原則，直到所有必要資源都列入白名單為止。 切換至是安全的 `restrict mode` 不再發生錯誤時。 否則，未妥善設定的CSP可能會導致瀏覽器顯示含有大量主控台錯誤的空白頁面。 正確設定的CSP可傳送白名單內容，而不會對效能造成任何影響。

**限制模式**：指示瀏覽器強制執行所有內容原則，並將發佈限制在白名單資源。 由於CSP是從伺服器（而非管理員）設定，因此大多數商家需要系統整合商或開發人員的協助才能正確設定。 另請參閱 [內容安全性原則](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 在 _Commerce PHP擴充功能_ 開發人員指南。

## 報告

依預設，CSP會將錯誤傳送至瀏覽器主控台，但可設定為透過HTTP要求收集錯誤記錄。 此外，您有數種協力廠商服務可用來監視、收集和報告CSP違規。

[報告URI](https://report-uri.io/) 是一項監視CSP違規並將結果顯示在儀表板中的服務。 商戶和開發人員都可以使用此服務，在發生CSP違規時接收報表。
