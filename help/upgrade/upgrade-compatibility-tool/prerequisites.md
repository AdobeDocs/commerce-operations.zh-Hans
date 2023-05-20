---
title: '''[!DNL Upgrade Compatibility Tool] 需求'
description: 確認您的系統符合執行 [!DNL Upgrade Compatibility Tool] 在Adobe Commerce專案的命令列介面中。
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce存取金鑰

{{commerce-only}}

您必須擁有 [Adobe Commerce存取金鑰](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 若要下載和使用 [!DNL Upgrade Compatibility Tool]. 將您的Adobe Commerce存取金鑰新增至 `auth.json` 檔案，位於 `~/.composer` 依預設。

>[!NOTE]
>
>檢查您的 **COMPOSER_HOME** 環境變數，以檢視 `auth.json` 檔案的位置。

此 **公開金鑰** 對應至 _使用者名稱_ 而 **私密金鑰** 是 _密碼_：

## Adobe Commerce存取金鑰範例

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> 如果您未正確設定 **Adobe Commerce存取金鑰**，您無法下載 [!DNL Upgrade Compatibility Tool] 和 `composer create-project` 命令將失敗。

執行 `composer install` 在終端機中安裝相依性。

## 系統需求

使用「 」的最低需求 [!DNL Upgrade Compatibility Tool] 在命令列介面中：

| **需求** | **限制** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| Composer | 沒有已知的需求。 |
| Node.js | Node.js版本 `^12.22.0`， `^14.17.0`，或 `>=16.0.0` (請參閱 [安裝Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| 記憶體限制 | 至少2GB RAM。 |

[!DNL Upgrade Compatibility Tool] 需要 [PCNTL](https://www.php.net/manual/en/book.pcntl.php) 和執行的其他PHP擴充功能。 使用以下專案檢查所需的PHP擴充功能 `composer check-platform-reqs` 命令：

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

只有Linux作業系統支援Adobe Commerce。 您可以執行 [!DNL Upgrade Compatibility Tool] 在Linux作業系統中。 您不必執行 [!DNL Upgrade Compatibility Tool] 您的Adobe Commerce執行個體所在的位置。

這是必要的 [!DNL Upgrade Compatibility Tool] 以存取Adobe Commerce例項的原始程式碼。 例如，您可以將其安裝在一部伺服器上，並將其指向另一部伺服器上的Adobe Commerce安裝。

如果您正在執行 [!DNL Upgrade Compatibility Tool] 針對具有大型模組和檔案的Adobe Commerce執行個體，此工具可能需要大量RAM （至少2GB）。

執行 [!DNL Upgrade Compatibility Tool] 從 [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) 的 [雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} 專案。
