---
title: 密码哈希处理
description: 请阅读有关密码哈希策略和实施的信息。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# 密码哈希处理

目前，Commerce基于不同的本机PHP哈希算法，使用其自己的密码哈希策略。 商务支持多种算法，例如 `MD5`, `SHA256`或 `Argon 2ID13`. 如果安装了Nade扩展（默认情况下在PHP 7.3中安装），则 `Argon 2ID13` 选择作为默认的哈希算法。 否则， `SHA256` 为默认值。 商务可以使用本机PHP `password_hash` 函数。

为了避免破坏使用过时算法(如 `MD5`，当前实施提供了一种无需更改原始密码即可升级哈希的方法。 通常，密码哈希的格式如下：

```text
password_hash:salt:version<n>:version<n>
```

其中 `version<n>`...`version<n>` 表示密码上使用的所有哈希算法版本。 同时，盐总是与口令哈希一起存储，这样我们就可以恢复整个算法链。 示例如下所示：

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

第一部分表示密码哈希。 第二， `8qnyO4H1OYIfGCUb` 盐。 最后两个是不同的哈希算法：1表示 `SHA256` 2表示 `Argon 2ID13`. 这意味着客户的密码最初是经过哈希处理的 `SHA256` 之后，算法将更新为 `Argon 2ID13` 哈希用氩气重新哈希处理。

## 升级哈希策略

请考虑哈希升级机制的外观。 假设最初，密码经过哈希处理 `MD5` 然后用Ar2ID13对算法进行多次更新。 下图显示了哈希升级流程。

![哈希升级工作流](../../assets/configuration/hash-upgrade-algorithm.png)

每个哈希算法都使用以前的密码哈希来生成一个新的哈希。 商务不存储原始原始密码。

![哈希升级策略](../../assets/configuration/hash-upgrade-strategy.png)

如上所述，密码哈希可能对原始密码应用了多个哈希版本。
以下是客户身份验证期间密码验证机制的工作方式。

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

由于商务将所有使用的密码哈希版本与密码哈希一起存储，所以在密码验证过程中可以恢复整个哈希链。 哈希验证机制与哈希升级策略类似：该算法根据与口令散列一起存储的版本，从提供的口令中生成哈希，并返回哈希口令与数据库存储的哈希之间的比较结果。

## 实施

的 `\Magento\Framework\Encryption\Encryptor` 类负责密码散列的生成和验证。 的 [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) 命令会将客户密码哈希升级为最新的哈希算法。
