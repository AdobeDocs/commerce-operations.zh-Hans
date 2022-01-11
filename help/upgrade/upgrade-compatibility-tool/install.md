---
title: 安装升级兼容性工具
description: 请按照以下步骤为您的Adobe Commerce项目安装升级兼容性工具。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 安装升级兼容性工具

升级兼容性工具是一个命令行工具，可通过分析其中安装的所有模块，根据特定版本检查Adobe Commerce自定义实例。 它会返回一个错误和警告列表，在升级到最新版本的Adobe Commerce之前，必须解决这些错误和警告。

## 工作流

下图显示了运行升级兼容性工具时的预期工作流程：

![升级兼容性工具图](../../assets/upgrade-guide/mvp-diagram-v3.png)

## 谁的升级兼容性工具？

以下用例介绍了Adobe Commerce合作伙伴升级客户端实例的典型流程：

1. 合作伙伴的软件工程师从 [Adobe Commerce存储库](https://repo.magento.com/) 并在最新Adobe Commerce版本的测试阶段执行它。 请参阅 [下载升级兼容性工具](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 主题以了解更多信息。
1. 软件工程师为当前安装的特定版本的Adobe Commerce生成一个原始实例。 请参阅 [参与者指南](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 有关使用 `instance` 命令生成香草安装。
1. 软件工程师发现清单和目录模块中有几个自定义区域被损坏，并且它们还获得X的复杂性分数。请参阅 [开发人员](../upgrade-compatibility-tool/developer.md) 指南，以了解有关复杂性分数的更多信息。
1. 利用此信息，软件工程师能够了解升级的复杂性，并能够将此信息转发给合作伙伴的客户经理。
1. 客户经理会为Adobe Commerce升级创建时间表和成本，以便获得经理的批准。
1. 经其经理批准后，软件工程师将进行所需的代码修改以修复损坏的模块。
1. 软件工程师在Adobe Commerce预发行版中再次运行升级兼容性工具，以确保没有新问题，并且其代码更改修复了测试阶段发现的问题。
1. 所有测试都会结束，软件工程师将代码推送到暂存环境，在该暂存环境中，回归测试确认所有测试均为绿色，这允许他们在Adobe Commerce预发行版发布的同一天将最新的Adobe Commerce版本发布到生产环境。

   ![升级兼容性工具受众](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>原版实例是特定版本的指定版本标记或分支的全新安装。

## 先决条件

请参阅 [先决条件](../upgrade-compatibility-tool/prerequisites.md) 以了解更多信息。

>[!NOTE]
>
>您可以在任何操作系统中运行升级兼容性工具。 无需运行Adobe Commerce实例所在的升级兼容性工具。 升级兼容性工具必须能够访问Adobe Commerce实例的源代码。 例如，您可以在一台服务器上安装该工具，并将其指向另一台服务器上的Adobe Commerce安装。

如果您针对具有大模块和文件的Adobe Commerce实例运行升级兼容性工具，则该工具可能需要大量RAM，至少需要2GB RAM。

### 建议的操作

Adobe Commerce最佳实践建议避免使用两个同名模块。 如果发生这种情况，升级兼容性工具会显示分段错误。

为避免出现此错误，建议运行 `bin` 的命令 `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>的 `<dir>` value是Adobe Commerce实例所在的目录。

的 `-m` 选项允许升级兼容性工具独立分析每个特定模块，以避免在Adobe Commerce实例中遇到两个同名模块。

此命令选项还允许升级兼容性工具分析包含多个模块的文件夹：

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

此建议还有助于解决在执行升级兼容性工具时可能发生的内存问题。

## 下载升级兼容性工具

要下载升级兼容性工具，请运行以下命令：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## 安装

要安装升级兼容性工具，您必须安装必要的先决条件：

* Adobe Commerce访问密钥
* 编辑器
* Node.js

### Adobe Commerce访问密钥

您必须 [Adobe Commerce访问密钥](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) 下载并使用升级兼容性工具。 将Adobe Commerce访问密钥添加到 `auth.json` 文件，位于 `~/.composer` 默认情况下。

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

克隆升级兼容工具存储库并运行 `composer install` 来安装依赖项。

>[!WARNING]
>
>如果 **Adobe Commerce访问密钥** 未正确配置，升级兼容工具将无法安装，并且您在运行 `composer install` 命令。

### Node.js

要安装Node.js，请参阅Node.js [文档](https://nodejs.dev/learn/how-to-install-nodejs).

## 第三方扩展

Adobe建议您联系扩展供应商以确定扩展是否与Adobe Commerce 2.4.x完全兼容。

请参阅 [运行工具](../upgrade-compatibility-tool/run.md) 有关执行升级兼容性工具的信息。
