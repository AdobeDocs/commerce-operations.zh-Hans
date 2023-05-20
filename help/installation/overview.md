---
title: 內部部署安裝概觀
description: 瞭解Adobe Commerce和Magento Open Source內部部署的安裝程式。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 內部部署安裝概觀

>[!NOTE]
>
>下圖提供下列專案的概觀 _**內部部署**_ Adobe Commerce和Magento Open Source的安裝：

![安裝如何運作](../assets/installation/install-diagram-24.svg)

一般安裝流程如下：

1. 設定您的伺服器環境。

   安裝先決條件軟體，包括PHP、Apache、MySQL和搜尋引擎。 請參閱 [系統需求](system-requirements.md) 以取得詳細資訊。

1. 取得 [驗證金鑰](prerequisites/authentication-keys.md) 至Commerce Composer存放庫。

1. 取得Adobe Commerce或Magento Open Source軟體。

   * （建議）取得 [Composer中繼套件](composer.md) 管理模組及其相依性。

   * 如果您想為Magento Open Source程式碼基底貢獻內容或自訂應用程式， [原地複製](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存放庫。 此方法需要熟悉GitHub和Composer。

1. 使用命令列安裝應用程式。

   如果步驟因必要條件軟體未正確設定而失敗，請檢閱 [必備條件](prerequisites/overview.md).

1. [驗證](next-steps/verify.md) 檢視您的店面和管理員以進行安裝。
