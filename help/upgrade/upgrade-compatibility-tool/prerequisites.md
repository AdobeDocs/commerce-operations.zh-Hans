---
title: '"[!DNL Upgrade Compatibility Tool] 要求”'
description: 验证您的系统是否满足运行 [!DNL Upgrade Compatibility Tool] 在命令行界面中。Adobe Commerce项目
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Adobe Commerce访问密钥

{{commerce-only}}

您必须 [Adobe Commerce访问密钥](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 下载和使用 [!DNL Upgrade Compatibility Tool]. 将Adobe Commerce访问密钥添加到 `auth.json` 文件，位于 `~/.composer` 默认情况下。

>[!NOTE]
>
>检查 **COMPOSER_HOME** 环境变量，以了解 `auth.json` 文件。

的 **公钥** 对应于 _用户名_ 而 **私钥** 是 _密码_:

## Adobe Commerce访问密钥示例

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
> 如果未正确配置 **Adobe Commerce访问密钥**，则无法下载 [!DNL Upgrade Compatibility Tool] 和 `composer create-project` 命令将失败。

运行 `composer install` 来安装依赖项。

## 系统要求

使用 [!DNL Upgrade Compatibility Tool] 在命令行界面中，为：

| **要求** | **约束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 编辑器 | 无已知要求。 |
| Node.js | Node.js版本 `^12.22.0`, `^14.17.0`或 `>=16.0.0` (请参阅 [安装Node.js](https://nodejs.dev/learn/how-to-install-nodejs)) |
| 内存限制 | 至少2GB内存。 |

[!DNL Upgrade Compatibility Tool] reamires [PCNTL](https://www.php.net/manual/en/book.pcntl.php) 和其他用于执行的PHP扩展。 使用检查所需的PHP扩展 `composer check-platform-reqs` 命令：

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

Adobe Commerce仅在Linux操作系统上受支持。 您可以运行 [!DNL Upgrade Compatibility Tool] 在Linux操作系统中。 您不必运行 [!DNL Upgrade Compatibility Tool] Adobe Commerce实例所在的位置。

对于 [!DNL Upgrade Compatibility Tool] 以访问Adobe Commerce实例的源代码。 例如，您可以在一台服务器上安装它，并将其指向另一台服务器上的Adobe Commerce安装。

如果您运行的是 [!DNL Upgrade Compatibility Tool] 对于具有大模块和文件的Adobe Commerce实例，该工具可能需要大量RAM（至少2 GB）。
