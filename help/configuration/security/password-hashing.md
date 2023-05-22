---
title: 密碼雜湊
description: 閱讀密碼雜湊策略與實作的相關資訊。
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 密碼雜湊

目前，Commerce根據不同的原生PHP雜湊演演算法，使用自己的密碼雜湊策略。 Commerce支援多種演演算法，例如 `MD5`， `SHA256`，或 `Argon 2ID13`. 如果已安裝Na延伸模組（預設安裝在PHP 7.3中），則 `Argon 2ID13` 被選為預設的雜湊演演算法。 否則， `SHA256` 為預設值。 Commerce可以使用原生PHP `password_hash` 函式搭配Argin 2i演演算法支援。

為了避免損害已使用過時演演算法(例如 `MD5`，目前的實作提供升級雜湊而不變更原始密碼的方法。 一般而言，密碼雜湊的格式如下：

```text
password_hash:salt:version<n>:version<n>
```

位置 `version<n>`...`version<n>` 代表密碼上使用的所有雜湊演演算法版本。 此外，Salt一律與密碼雜湊一起儲存，因此我們可以還原整個演演算法鏈。 範例如下所示：

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

第一部分代表密碼雜湊。 第二， `8qnyO4H1OYIfGCUb` 是鹽。 最後兩個是不同的雜湊演演算法：1是 `SHA256` 而2是 `Argon 2ID13`. 這表示客戶的密碼原本是透過雜湊處理 `SHA256` 之後，演演算法更新為 `Argon 2ID13` 然後用Argon重新整理雜湊。

## 升級雜湊策略

請考量雜湊升級機制的外觀。 假設密碼原本是透過雜湊處理 `MD5` 然後使用Argin 2ID13多次更新演演算法。 下圖顯示雜湊升級流程。

![雜湊升級工作流程](../../assets/configuration/hash-upgrade-algorithm.png)

每個雜湊演演算法都會使用先前的密碼雜湊來產生新的雜湊。 Commerce不會儲存原始密碼。

![雜湊升級策略](../../assets/configuration/hash-upgrade-strategy.png)

如上所述，密碼雜湊可能會套用多個雜湊版本至原始密碼。
以下說明密碼驗證機制在客戶驗證期間的運作方式。

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

由於Commerce會將所有使用的密碼雜湊版本與密碼雜湊一起儲存，因此我們可以在密碼驗證期間還原整個雜湊鏈。 雜湊驗證機制類似於雜湊升級策略：演演算法會根據與密碼雜湊一起儲存的版本，從提供的密碼產生雜湊，並傳回雜湊密碼與資料庫儲存雜湊的比較結果。

## 實作

此 `\Magento\Framework\Encryption\Encryptor` 類別負責密碼雜湊產生和驗證。 此 [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) 命令會將客戶密碼雜湊升級為最新的雜湊演演算法。
