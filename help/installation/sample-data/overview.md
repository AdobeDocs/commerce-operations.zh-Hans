---
title: 範例資料概述
description: 瞭解如何針對Adobe Commerce和Magento Open Source專案使用範例資料。
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 範例資料概述

範例資料提供以Luma主題為基礎的店面，並搭配產品、類別、客戶註冊等。 它的功能就像一個Commerce店面，您可以使用管理員來控制價格、庫存和促銷定價規則。

您可以在安裝Commerce軟體之前或之後安裝範例資料。 使用完範例資料後，您可以將其移除或全新安裝，如中所述 [移除範例資料模組或更新範例資料](remove-or-update.md).

>[!WARNING]
>
>您無法解除安裝範例資料。 建議您只使用範例資料，以瞭解Adobe Commerce和Magento Open Source的運作方式。 請避免在您已安裝範例資料的系統中進行任何開發。

您可以透過下列任何方式安裝選用的範例資料：

| 安裝方法 | 說明 | 所需技能等級 |
|--- |--- |--- |
| 使用撰寫器 | [執行 `magento sampledata:deploy` 修改應用程式的根目錄 `composer.json`](composer-packages.md) 以啟用範例資料模組。 | 需要Composer知識以及商務檔案系統的存取權。 |
| 複製存放庫 | [複製GitHub存放庫](git-repositories.md) 和範例資料存放庫建立連結，然後將兩者連結在一起。 | 僅供貢獻開發人員使用。 其他所有人都應使用上述其中一種方法。 |
