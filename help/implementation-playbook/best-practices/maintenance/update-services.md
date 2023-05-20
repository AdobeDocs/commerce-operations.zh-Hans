---
title: 更新服務最佳實務
description: 瞭解如何保持雲端基礎結構技術棧疊上的Adobe Commerce更新。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 更新服務最佳實務

本文提供建議讓雲端基礎結構技術棧疊上的Adobe Commerce保持更新，並提供實用資源的連結。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.4.x和更新版本

## 更新服務

在Adobe Commerce使用的服務和元件達到或接近其生命週期結束日期之前，請升級這些服務和元件。 這有助於遵循PCI法規並減少安全性漏洞。

入門計畫客戶可自助服務升級。 請參閱 [變更服務版本](https://devdocs.magento.com/cloud/project/services.html#change-service-version) 以取得如何執行此動作的詳細資訊。

Pro計畫的客戶只能自助服務升級其服務 [整合環境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). 若要在生產環境中升級服務，您必須 [提交支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 要求升級。

>[!WARNING]
>
>若未提前48個營業時間通知我們的基礎建設團隊，服務升級便無法推送至生產環境。 由於我們需要確保我們提供基礎架構支援工程師，以在所需時間範圍內更新您的設定，並將生產環境的停機時間降至最低，因此我們有必要採取此做法。

您可以在下列檔案中檢視服務版本和生命週期結束日期的清單： [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>此檔案不可以視為單一信任來源。 如有疑問，請參閱官方廠商網站以瞭解這些技術。

## 其他資訊

[系統需求](../../../installation/system-requirements.md)
