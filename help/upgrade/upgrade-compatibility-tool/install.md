---
title: 安装 [!DNL Upgrade Compatibility Tool]
description: 按照以下步骤安装 [!DNL Upgrade Compatibility Tool] 为您的Adobe Commerce项目。
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# 安装 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

的 [!DNL Upgrade Compatibility Tool] 是一个命令行工具，可通过分析Adobe Commerce中安装的所有模块，根据特定版本检查某个特定版本的自定义实例。 它会返回一个错误和警告列表，在升级到最新版本的Adobe Commerce之前，必须解决这些错误和警告。

## 下载 [!DNL Upgrade Compatibility Tool]

要下载 [!DNL Upgrade Compatibility Tool]，运行以下命令：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## 安装

安装 [!DNL Upgrade Compatibility Tool]，则必须安装必要的先决条件：

* Adobe Commerce访问密钥
* 编辑器
* Node.js

## 先决条件

请参阅 [先决条件](../upgrade-compatibility-tool/prerequisites.md) 以了解更多信息。

### Adobe Commerce访问密钥

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

### 编辑器

克隆 [!DNL Upgrade Compatibility Tool] 存储库和运行 `composer install` 来安装依赖项。

>[!WARNING]
>
>如果 **Adobe Commerce访问密钥** 未正确配置， [!DNL Upgrade Compatibility Tool] 将不安装，并且在运行 `composer install` 命令。

### Node.js

要安装Node.js，请参阅Node.js [文档](https://nodejs.dev/learn/how-to-install-nodejs).

## 第三方扩展

Adobe建议您联系扩展供应商以确定您的扩展是否与Adobe Commerce最新版本完全兼容。

请参阅 [运行工具](../upgrade-compatibility-tool/run.md) 有关执行 [!DNL Upgrade Compatibility Tool].
