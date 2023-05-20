---
title: 最佳化影像，以建立回應速度更快的網站
description: 瞭解最佳化影像的步驟，並使用Fastly影像最佳化來最佳化Adobe Commerce網站上的回應時間。
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# 最佳化影像，以建立回應速度更快的網站

針對雲端基礎結構部署的Adobe Commerce，請先最佳化影像再上傳檔案，即可縮短網站回應時間。 然後，使用Fastly影像最佳化來加速影像傳送並簡化影像來源集的維護。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

雲端基礎結構上的Adobe Commerce


## 最佳化和壓縮影像

在將影像上傳到您的Commerce網站之前，請最佳化和壓縮影像，以平衡效能和檢視品質。 這有助於增加空間並減少頁面載入時間。

- PNG格式可針對具有大面積純色區域的影像提供較小大小的影像。

- JPEG格式可為所有其他影像型別提供較小大小的影像。 使用最高壓縮率（不會明顯降低）。 這通常是60%到80%。

## 啟用和設定Fastly影像最佳化

在您為Adobe Commerce Cloud專案設定Fastly服務後，請參閱 [Fastly影像最佳化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) 以取得啟用和設定影像最佳化的指示。

## 其他資訊

- [設定Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [最佳化不良的影像可能會導致效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
