---
title: 防止快取中毒
description: 瞭解如何防止您的Commerce店面出現頁面快取中毒。
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 防止快取中毒

本主題說明使用Microsoft Internet Information Server (IIS)網頁伺服器時，如何防止快取中毒。 _快取中毒_ 是一種變更快取內容以包含相同網站中不同頁面的方法。 例如，可以插入HTTP 404 （找不到）錯誤頁面來取代某些良性頁面（例如店面首頁），這可能會導致潛在的拒絕服務(DoS)。 惡意頁面URL會由Varnish或Redis快取，因此命名為 _頁面快取中毒_.

這些型別的攻擊可能難以偵測，因為它們不會導致網頁伺服器記錄錯誤。

此解決方案適用於下列Commerce版本：

- 2.0.10和更新版本
- 2.1.2和更新版本

>[!INFO]
>
>本主題適用於經驗豐富的IIS管理員。

## 說明

如果IIS伺服器上啟用了URL重寫，且在請求到達Varnish或Redis快取服務之前變更了以下任何HTTP標頭，則會導致此問題：

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

如果變更這些標頭，則會快取產生的URL和內容，導致潛在的漏洞。

## 解決方案

我們提供的選項會根據的IIS伺服器設定移除所有先前標題的值 `Enable_IIS_Rewrites`.

- 若 `Enable_IIS_Rewrites` 設為 `0`，則會移除標題的值。
- 若 `Enable_IIS_Rewrites` 設為 `1`，標題的值保持不變。

>[!WARNING]
>
>如果您設定 `Enable_IIS_Rewrites` 至 `1`，您不得在要求送達IIS網頁伺服器之前變更前述標頭的值。
