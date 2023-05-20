---
title: 取得您的驗證金鑰
description: 請依照以下步驟擷取憑證以存取repo.magento.com上的Adobe Commerce和Magento Open Source撰寫器套件。
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# 取得您的驗證金鑰

此 `repo.magento.com` 存放庫是儲存Adobe Commerce和Magento Open Source及協力廠商撰寫器套件的位置，且需要驗證。 使用您的Commerce Marketplace帳戶產生一對32個字元 *驗證金鑰* 以存取存放庫。

若要存取Adobe Commerce和Magento Open Source套件的許可權，您必須使用與已授予這些套件存取許可權的MAGEID相關聯的金鑰。 MAGEID通常是Adobe Commerce帳戶的主要聯絡人，可能並不一定都是Adobe Commerce on cloud infrastructure專案的專案所有者。

>[!TIP]
>
>如果您遇到 [錯誤](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)，您可能沒有存取該套件的授權，或者存取許可權已過期，因為您的帳戶有未結的發票。
>
>* 若您是該帳戶的「主要聯絡人」，請確定該帳戶上未列出未結商業發票。
>* 如果主要連絡人提供的金鑰無法運作，且帳戶中沒有未結商業發票，請連絡 [Adobe Commerce支援](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 以取得使用主要連絡人MAGEID的協助。


若要建立驗證金鑰：

1. 登入 [Commerce Marketplace](https://marketplace.magento.com). 如果您沒有帳戶，請按一下 **註冊**.
1. 按一下頁面右上方的帳戶名稱，然後選取 **我的設定檔**.

1. 按一下 **存取金鑰** 在Marketplace索引標籤中。

   ![在Commerce Marketplace上取得您的安全存取金鑰](../../assets/installation/cloud_access-key.png)

1. 按一下 **建立新的存取金鑰**. 輸入金鑰的特定名稱（例如，接收金鑰的開發人員姓名），然後按一下 **確定**.

1. 新的公開和私密金鑰現在與您的帳戶相關聯，您可以按一下以複製。 儲存此資訊或在使用專案時保持頁面開啟。 使用 **公開金鑰** 作為您的使用者名稱和 **私密金鑰** 作為您的密碼。

## 管理您的驗證金鑰

您也可以停用或刪除驗證金鑰。 例如，在某人離開您的組織後，您可以基於安全考量停用或刪除金鑰。

* 若要停用金鑰：按一下 **停用**. 如果要暫停使用金鑰，可以執行此操作。
* 若要啟用先前停用的金鑰：按一下 **啟用**.
* 若要刪除金鑰：按一下 **刪除**.

### 管理SSH存取權杖

若要使用SSH下載Adobe Commerce版本，您必須產生下載存取權杖。 若要產生Token：

1. 登入您的 [magento.com帳戶](https://account.magento.com/customer/account/login).
1. 按一下 **我的帳戶** ，位於頁面頂端。
1. 按一下 **帳戶設定** > **下載存取Token**.

   ![存取您的金鑰](../../assets/installation/connect_keys1.png)

1. 按一下 **產生新Token** 以取代和停用現有的Token。

您必須使用MAGEID和Token來下載版本。 您的MAGEID會顯示在帳戶頁面的左上方。

例如：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

使用您的驗證金鑰來：

* [取得中繼資料（整合商、封裝商）](../composer.md)
* [複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) （僅限貢獻開發人員）
* [升級和管理模組](../../upgrade/modules/upgrade.md)
