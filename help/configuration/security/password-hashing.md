---
title: 密码散列
description: 阅读有关密码哈希处理策略和实施的信息。
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 密码散列

目前，Commerce使用自己的密码哈希处理策略，基于不同的本机PHP哈希算法。 Commerce支持多种算法，例如 `MD5`， `SHA256`，或 `Argon 2ID13`. 如果已安装Na扩展（缺省情况下安装在PHP 7.3中），则 `Argon 2ID13` 被选为默认的哈希算法。 否则， `SHA256` 为默认值。 Commerce可以使用本机PHP `password_hash` 函数支持Argin 2i算法。

为了避免影响使用过时的算法（如）散列后的旧密码 `MD5`，则当前实施提供了一种方法，无需更改原始密码即可升级哈希。 通常，密码散列的格式如下：

```text
password_hash:salt:version<n>:version<n>
```

位置 `version<n>`...`version<n>` 表示对密码使用的所有哈希算法版本。 而且，Salt始终与密码哈希一起存储，因此我们可以还原整个算法链。 示例如下所示：

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

第一部分表示口令哈希。 第二， `8qnyO4H1OYIfGCUb` 是盐。 后两种是不同的哈希算法： 1是 `SHA256` 和2是 `Argon 2ID13`. 这意味着客户的密码最初是使用进行哈希处理的 `SHA256` 之后，算法更新为 `Argon 2ID13` 然后用氩气把杂凑整齐了。

## 升级哈希策略

请考虑哈希升级机制是什么样的。 假设最初对密码进行了哈希处理 `MD5` 然后用Argin 2ID13对算法进行了多次更新。 下图显示了哈希升级流程。

![哈希升级工作流](../../assets/configuration/hash-upgrade-algorithm.png)

每个哈希算法都使用以前的密码哈希来生成新的哈希。 Commerce不会存储原始原始密码。

![哈希升级策略](../../assets/configuration/hash-upgrade-strategy.png)

如上所述，密码哈希可能具有多个应用于原始密码的哈希版本。
下面是密码验证机制在客户身份验证期间的工作方式。

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

由于Commerce将所有使用的密码哈希版本与密码哈希一起存储，因此可以在密码验证期间还原整个哈希链。 哈希验证机制类似于哈希升级策略：根据与口令哈希一起存储的版本，算法从提供的口令生成哈希并返回哈希口令与数据库存储的哈希的比较结果。

## 实现

此 `\Magento\Framework\Encryption\Encryptor` 类负责密码哈希的生成和验证。 此 [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) 命令将客户密码哈希升级为最新的哈希算法。
