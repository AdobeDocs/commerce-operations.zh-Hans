---
title: ’[!DNL Upgrade Compatibility Tool] 要求
description: 验证系统是否符合运行 [!DNL Upgrade Compatibility Tool] 在Adobe Commerce项目的命令行界面中。
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce访问密钥

{{commerce-only}}

您必须拥有 [Adobe Commerce访问密钥](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 要下载和使用 [!DNL Upgrade Compatibility Tool]. 将您的Adobe Commerce访问密钥添加到 `auth.json` 文件，位于 `~/.composer` 默认情况下。

>[!NOTE]
>
>检查您的 **COMPOSER_HOME** 环境变量，以查看 `auth.json` 文件所在位置。

此 **公钥** 对应于 _用户名_ 而 **私钥** 是 _密码_：

## Adobe Commerce访问键示例

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
> 如果未正确配置 **Adobe Commerce访问密钥**，您无法下载 [!DNL Upgrade Compatibility Tool] 和 `composer create-project` 命令将失败。

运行 `composer install` 在终端中安装依赖项。

## 系统要求

使用 [!DNL Upgrade Compatibility Tool] 在命令行界面中：

| **要求** | **约束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| Composer | 没有已知要求。 |
| Node.js | Node.js版本 `^12.22.0`， `^14.17.0`，或 `>=16.0.0` (请参阅 [安装节点.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| 内存限制 | 至少2GB RAM。 |

[!DNL Upgrade Compatibility Tool] 需要 [PCNTL](https://www.php.net/manual/en/book.pcntl.php) 以及执行的其他PHP扩展。 使用以下方式检查所需的PHP扩展 `composer check-platform-reqs` 命令：

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

Adobe Commerce仅在Linux操作系统上受支持。 您可以运行 [!DNL Upgrade Compatibility Tool] 在Linux操作系统中。 您不必运行 [!DNL Upgrade Compatibility Tool] Adobe Commerce实例的位置。

对于 [!DNL Upgrade Compatibility Tool] 以访问Adobe Commerce实例的源代码。 例如，您可以将其安装在一台服务器上，并将其指向另一台服务器上的Adobe Commerce安装。

如果您正在运行 [!DNL Upgrade Compatibility Tool] 对于具有大型模块和文件的Adobe Commerce实例，该工具可能需要大量RAM（至少2GB）。

运行 [!DNL Upgrade Compatibility Tool] 从 [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) 对象 [云基础架构上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} 项目。
