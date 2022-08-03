---
title: '"[!DNL Upgrade Compatibility Tool] 要求”'
description: '验证您的系统是否满足运行 [!DNL Upgrade Compatibility Tool] 在命令行界面中。Adobe Commerce项目 '
source-git-commit: 7ec999f9122eb0707ac6c37b7b49f9c423945318
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Adobe Commerce访问密钥

{{commerce-only}}

您必须 [Adobe Commerce访问密钥](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) 下载和使用 [!DNL Upgrade Compatibility Tool]. 将Adobe Commerce访问密钥添加到 `auth.json` 文件，位于 `~/.composer` 默认情况下。

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

Adobe Commerce仅在Linux操作系统上受支持。 您可以运行 [!DNL Upgrade Compatibility Tool] 在Linux操作系统中。 您不必运行 [!DNL Upgrade Compatibility Tool] Adobe Commerce实例所在的位置。

对于 [!DNL Upgrade Compatibility Tool] 以访问Adobe Commerce实例的源代码。 例如，您可以在一台服务器上安装它，并将其指向另一台服务器上的Adobe Commerce安装。

如果您运行的是 [!DNL Upgrade Compatibility Tool] 对于具有大模块和文件的Adobe Commerce实例，该工具可能需要大量RAM（至少2 GB）。
