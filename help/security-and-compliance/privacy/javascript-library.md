---
title: 隱私權JavaScript程式庫
description: 瞭解如何使用自訂工具來存取和刪除Adobe Commerce和Magento Open Source收集的客戶個人資訊。
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# 隱私權JavaScript程式庫

隱私權JavaScript程式庫是一組工具，可協助建立存取和刪除Adobe Commerce和Magento Open Source所收集私人資料的程式。

Commerce資料追蹤服務可儲存適用於隱私權法規的私人資訊，例如 [一般資料保護規範(GDPR)](gdpr.md) 和 [加州消費者隱私法(CCPA)](ccpa.md).

此程式庫提供一組功能，用於建立隱私權資料請求及收集其回應。 使用此資料庫可擷取和移除Adobe Commerce和Magento Open Source資料追蹤服務儲存在瀏覽器中的資料。

>[!NOTE]
>
>若 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 已啟用，在購物者同意之前，Commerce不會收集行為資料。 若 [!UICONTROL **Cookie限制模式**] 停用，Commerce會依預設收集行為資料。

## 安裝

隱私權JavaScript程式庫可在下列CDN位置取得： `commerce.adobe.net/magentoprivacy.js`

取得檔案後，您需要將其新增到安裝在Adobe Commerce或Magento Open Source執行個體中的自訂模組或主題。 請依照以下說明操作： [使用自訂JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 完成此任務的主題。

### 初始化

匯入並例項化新的 `MagentoPrivacy` 物件或使用 `window` 物件以存取隱私權JavaScript函式。

使用的範例 `import`：

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

使用的範例 `window`：

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用狀況

隱私權JS資料庫提供多種功能，可管理儲存在瀏覽器中的身分資料。

`retrieveIdentity()`
：從瀏覽器中的服務傳回身分物件的JavaScript Promise。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
：從瀏覽器中的服務移除身分資料。
此函式傳回身分物件的JavaScript Promise，其中包含 `isDeleted` 指示資料是否已刪除的布林屬性。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
