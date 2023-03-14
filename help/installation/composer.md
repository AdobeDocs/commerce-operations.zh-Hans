---
title: 快速启动内部部署
description: 按照以下步骤在您拥有的基础架构上安装Adobe Commerce或Magento Open Source。
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---


# 快速启动内部部署

我们使用 [Composer](https://getcomposer.org/) 管理Adobe Commerce和Magento Open Source组件及其依赖项。 使用编辑器获取Adobe Commerce和Magento Open Source [隐含](https://glossary.magento.com/metapackage) 具有以下优势：

- 重用第三方库，而无需将它们与源代码捆绑在一起
- 通过使用基于组件的架构和强大的依赖关系管理，减少扩展冲突和兼容性问题
- 遵守 [PHP框架互操作性小组(FIG)](https://www.php-fig.org/) 标准
- 将Magento Open Source与其他组件重新打包
- 在生产环境中使用Adobe Commerce或Magento Open Source软件

>[!NOTE]
>
>对Magento Open Source有贡献的开发人员应使用 [基于Git](https://developer.adobe.com/commerce/contributor/guides/install/) 安装方法。

## 先决条件

在继续之前，您必须执行以下操作：

- 全部完成 [先决任务](system-requirements.md).
- [安装编辑器](https://getcomposer.org/download/).
- Get [身份验证密钥](prerequisites/authentication-keys.md) 到Adobe Commerce和Magento Open Source编辑器存储库。

## 以文件系统所有者的身份登录

了解所有权、权限和文件系统所有者，请参见 [所有权和权限主题概述](prerequisites/file-system/overview.md).

切换到文件系统所有者：

1. 以具有写入文件系统权限的用户身份登录或切换到应用程序服务器。

   如果使用bash shell，则可以使用以下语法切换到文件系统所有者并同时输入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果文件系统所有者不允许登录，您可以执行以下操作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 要从任何目录运行CLI命令，请添加 `<app_root>/bin` 到您的系统 `PATH`.

   由于外壳的语法不同，请查阅参考资料，如 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS的bash shell示例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   或者，也可以以下列方式运行命令：

   - `cd <app_root>/bin` 并运行它们 `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` 是Web服务器docroot的子目录

## 获取暗喻

要获取Adobe Commerce或Magento Open Source隐喻，请执行以下操作：

1. 以或切换至以下身份登录到应用程序服务器： [文件系统所有者](prerequisites/file-system/overview.md).
1. 转到Web服务器docroot目录或您已配置为虚拟主机docroot的目录。
1. 使用Adobe Commerce或Magento Open Source元包创建编辑器项目。

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出现提示时，输入您的身份验证密钥。 可在中创建和配置公钥和私钥 [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   如果您遇到错误，例如 `Could not find package...` 或 `...no matching package found`，确保命令中没有拼写错误。 如果您仍然遇到错误，则可能无权下载Adobe Commerce。 联系人 [Adobe Commerce支持](https://support.magento.com/hc/en-us) 以寻求帮助。

   参见 [疑难解答](https://support.magento.com/hc/en-us/articles/360033818091) 以获取有关更多错误的帮助。

   >[!NOTE]
   >
   >Adobe Commerce客户可以在正式发布(GA)日期的两周前访问修补程序。 预发行版软件包只能通过Composer获得。 在GA之前，您无法在开发人员门户或GitHub上访问预发行版。 如果您在编辑器中找不到这些包，请联系Adobe Commerce支持。

### 示例 — 次要版本

次要版本包含新功能、质量修复和安全修复。 使用Composer指定次要版本。 例如，要指定Adobe Commerce 2.4.5元包，请执行以下操作：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### 示例 — 质量修补程序

质量补丁主要包含功能性 _和_ 安全修复。 但是，它们有时也可以包含向后兼容的新功能。 使用Composer下载高质量的修补程序。 例如，要指定Adobe Commerce 2.4.5元包，请执行以下操作：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### 示例 — 安全修补程序

安全修补程序仅包含安全修补程序。 它们旨在使升级过程更快、更轻松。

安全修补程序使用编辑器命名约定 `2.4.5-px`. 使用Composer指定修补程序。 例如，要下载Adobe Commerce 2.4.5-p1中继，请执行以下操作：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5-p1 <install-directory-name>
```

## 设置文件权限

在安装Adobe Commerce或Magento Open Source之前，必须设置Web服务器组的读写权限。 这是必要的，以便命令行可以将文件写入文件系统。

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## 安装应用程序

您必须使用命令行安装Adobe Commerce或Magento Open Source。

此示例假定安装目录名为 `magento2ee`，则 `db-host` 在同一台计算机上(`localhost`)，并且 `db-name`， `db-user`、和 `db-password` 全部 `magento`：

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>您可以使用自定义管理员URI `--backend-frontname` 选项。 但是，我们建议忽略此选项，并允许安装命令自动生成随机URI。 黑客或恶意软件更难利用随机URI。 安装完成后，控制台中会显示URI。

>[!TIP]
>
>有关CLI安装选项的完整说明，请参见 [从命令行安装应用程序](advanced.md).

## 命令摘要

要显示完整的命令列表，请输入：

```bash
bin/magento list
```

要获取特定命令的帮助，请输入：

```bash
bin/magento help <command>
```

例如：

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

下表总结了可用的命令。 命令仅以摘要形式显示。 有关命令的详细信息，请单击“命令”列中的链接。

| 命令 | 描述 | 先决条件 |
|--- |--- |--- |
| `magento setup:install` | 安装应用程序 | 无 |
| `magento setup:uninstall` | 删除应用程序。 | 已安装应用程序 |
| `magento setup:upgrade` | 更新应用程序。 | 部署配置 |
| `magento maintenance:{enable/disable}` | 启用或禁用维护模式（在维护模式下，只有免费IP地址才能访问管理员或店面）。 | 已安装应用程序 |
| `magento setup:config:set` | 创建或更新部署配置。 | 无 |
| `magento module:{enable/disable}` | 启用或禁用模块。 | 无 |
| `magento setup:store-config:set` | 设置与店面相关的选项，如基本URL、语言、时区。 | 部署配置 |
| `magento setup:db-schema:upgrade` | 更新数据库模式。 | 部署配置 |
| `magento setup:db-data:upgrade` | 更新数据库数据。 | 部署配置 |
| `magento setup:db:status` | 检查数据库是否使用代码保持最新。 | 部署配置 |
| `magento admin:user:create` | 创建管理员用户。 | 您可以为以下内容创建用户：<br><br>部署配置<br><br>至少启用 `Magento_User` 和 `Magento_Authorization` 模块<br><br>数据库(最简单的方法是使用 `bin/magento setup:upgrade`) |
| `magento list` | 列出所有可用命令。 | 无 |
| `magento help` | 提供指定命令的帮助。 | 无 |

### 常用参数

以下参数对所有命令都是通用的。 这些命令可以在安装应用程序之前或之后运行：

| 长版本 | 简短版本 | 含义 |
|--- |--- |--- |
| `--help` | `-h` | 获取任何命令的帮助。 例如， `./magento help setup:install` 或 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 安静模式；无输出。 |
| `--no-interaction` | `-n` | 无交互式问题。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 详细级别。 例如， `--verbose=3` 或 `-vvv` 显示调试详细程度，这是最详细的输出。 默认为 `--verbose=1` 或 `-v`. |
| `--version` | `-V` | 显示此应用程序版本 |
| `--ansi` | 不适用 | 强制ANSI输出 |
| `--no-ansi` | 不适用 | 禁用ANSI输出 |

>[!NOTE]
>
>恭喜！ 您已完成快速安装。 是否需要更多高级帮助？ 查看我们的 [高级安装](advanced.md) 指南。
