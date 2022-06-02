---
title: '"[!DNL Upgrade Compatibility Tool] 要求”'
description: '验证您的系统是否满足运行 [!DNL Upgrade Compatibility Tool] 为您的Adobe Commerce项目。 '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 系统要求

{{commerce-only}}

使用 [!DNL Upgrade Compatibility Tool] 为：

| **要求** | **约束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 编辑器 | 无已知要求 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`或 `>=16.0.0`) |
| 内存限制 | 至少2GB RAM |

您可以运行 [!DNL Upgrade Compatibility Tool] （不支持Windows）。 您不必运行 [!DNL Upgrade Compatibility Tool] Adobe Commerce实例所在的位置。

对于 [!DNL Upgrade Compatibility Tool] 以访问Adobe Commerce实例的源代码。 例如，您可以在一台服务器上安装它，并将其指向另一台服务器上的Adobe Commerce安装。

如果您运行的是 [!DNL Upgrade Compatibility Tool] 对于具有大模块和文件的Adobe Commerce实例，该工具可能需要大量RAM（至少2 GB）。

## Adobe Commerce访问密钥

您必须 [Adobe Commerce访问密钥](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) 下载和使用 [!DNL Upgrade Compatibility Tool]. 将Adobe Commerce访问密钥添加到 `auth.json` 文件，位于 `~/.composer` 默认情况下。

>[!WARNING]
>
>检查 **COMPOSER_HOME** 环境变量，以了解 `auth.json` 文件。

的 **公钥** 对应于 _用户名_ 而 **私钥** 是 _密码_:

### Adobe Commerce访问密钥示例

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

## 编辑器

下载 [!DNL Upgrade Compatibility Tool] 存储库和运行 `composer install` 来安装依赖项。

>[!NOTE]
>
> 如果未正确配置 **Adobe Commerce访问密钥**，则无法下载 [!DNL Upgrade Compatibility Tool]. 运行 `composer create-project` 命令将失败。

## Node.js

要安装Node.js，请参阅Node.js [文档](https://nodejs.dev/learn/how-to-install-nodejs).

## 第三方扩展

Adobe建议您联系扩展供应商以确定扩展是否与最新版本的Adobe Commerce完全兼容。
