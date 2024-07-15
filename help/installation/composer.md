---
title: 快速启动内部部署
description: 按照以下步骤在您拥有的基础架构上安装Adobe Commerce。
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# 快速启动内部部署

本页上的说明介绍了如何在[自托管](../implementation-playbook/infrastructure/self-hosting/overview.md)基础架构上安装Adobe Commerce。 有关升级现有安装的指导，请参阅&#x200B;[_升级指南_](../upgrade/overview.md)。

Adobe使用[Composer](https://getcomposer.org/)管理Adobe Commerce组件及其依赖项。 使用Composer获取Adobe Commercemetapackage具有以下优势：

- 重用第三方库，而无需将它们与源代码捆绑在一起
- 通过使用基于组件的架构和强大的依赖关系管理，减少扩展冲突和兼容性问题
- 遵守[PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)标准
- 使用其他组件重新打包Magento Open Source
- 在生产环境中使用Adobe Commerce软件

>[!NOTE]
>
>参与Magento Open Source的开发人员应使用基于[Git的](https://developer.adobe.com/commerce/contributor/guides/install/)安装方法。

## 先决条件

在继续之前，必须执行以下操作：

- 完成所有[必备任务](system-requirements.md)。
- [安装编辑器](https://getcomposer.org/download/)。
- 将[身份验证密钥](prerequisites/authentication-keys.md)获取到Adobe Commerce Composer存储库。

## 以文件系统所有者的身份登录

在[所有权和权限概述主题](prerequisites/file-system/overview.md)中了解所有权、权限和文件系统所有者。

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

1. 若要从任何目录运行CLI命令，请将`<app_root>/bin`添加到您的系统`PATH`。

   由于shell具有不同的语法，请查阅[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)之类的引用。

   CentOS的bash shell示例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   或者，也可以通过以下方式运行命令：

   - `cd <app_root>/bin`并作为`./magento <command name>`运行
   - `app_root>/bin/magento <command name>`
   - `<app_root>`是Web服务器docroot的子目录

## 获取隐喻

要获取Adobe Commerce的比喻，请执行以下操作：

1. 以[文件系统所有者](prerequisites/file-system/overview.md)的身份登录或切换到您的应用程序服务器。
1. 转到Web服务器docroot目录或您已配置为虚拟主机docroot的目录。
1. 使用Commerce隐喻创建编辑器项目。

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出现提示时，输入您的身份验证密钥。 在[Commerce Marketplace](https://commercemarketplace.adobe.com/customer/account/login/)中创建并配置公钥和私钥。

   >[!NOTE]
   >
   > 使用编辑器`auth.json`文件或环境变量时，系统不会提示您输入身份验证密钥。

   如果遇到错误（如`Could not find package...`或`...no matching package found`），请确保命令中没有拼写错误。 如果仍遇到错误，则可能无权下载Adobe Commerce。 请联系[Adobe Commerce支持](https://support.magento.com/hc/en-us)以获取帮助。

   请参阅[疑难解答](https://support.magento.com/hc/en-us/articles/360033818091)以获取更多错误的帮助。

### 示例 — 次要版本

次发行版本包含新功能、质量修复和安全修复。 使用编辑器指定次要版本。 例如，要指定Adobe Commerce 2.4.6metapackage，请执行以下操作：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 示例 — 质量修补程序

质量修补程序主要包含功能性&#x200B;_和_&#x200B;安全修补程序。 但是，它们有时也可以包含向后兼容的新功能。 使用Composer下载质量修补程序。 例如，要指定Adobe Commerce 2.4.6metapackage，请执行以下操作：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 示例 — 安全修补程序

安全修补程序仅包含安全修补程序。 它们旨在使升级过程更快、更轻松。

安全修补程序使用Composer命名约定`2.4.6-px`。 使用Composer指定修补程序。 例如，要下载Adobe Commerce 2.4.6-p1中继包，请执行以下操作：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## 设置文件权限

在安装Adobe Commerce之前，必须设置Web服务器组的读写权限。 这是必要的，以便命令行可以将文件写入文件系统。

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## 安装应用程序

您必须使用命令行安装Adobe Commerce。

此示例假定安装目录名为`magento2ee`，`db-host`在同一计算机(`localhost`)上，`db-name`、`db-user`和`db-password`均为`magento`：

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
>您可以使用`--backend-frontname`选项自定义管理员URI。 但是，Adobe建议忽略此选项，并允许安装命令自动生成随机URI。 黑客或恶意软件更难利用随机URI。 安装完成后，控制台中会显示URI。

>[!TIP]
>
>有关CLI安装选项的完整说明，请参阅[从命令行安装应用程序](advanced.md)。

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
| `magento setup:store-config:set` | 设置店面相关选项，如基本URL、语言、时区。 | 部署配置 |
| `magento setup:db-schema:upgrade` | 更新数据库模式。 | 部署配置 |
| `magento setup:db-data:upgrade` | 更新数据库数据。 | 部署配置 |
| `magento setup:db:status` | 检查数据库是否使用代码保持最新。 | 部署配置 |
| `magento admin:user:create` | 创建管理员用户。 | 您可以为以下内容创建用户：<br><br>部署配置<br><br>至少启用`Magento_User`和`Magento_Authorization`个模块<br><br>数据库（最简单的方法是使用`bin/magento setup:upgrade`） |
| `magento list` | 列出所有可用命令。 | 无 |
| `magento help` | 提供指定命令的帮助。 | 无 |

### 常用参数

以下参数对所有命令都是通用的。 这些命令可以在安装应用程序之前或之后运行：

| 长版本 | 简短版本 | 含义 |
|--- |--- |--- |
| `--help` | `-h` | 获取任何命令的帮助。 例如，`./magento help setup:install`或`./magento help setup:config:set`。 |
| `--quiet` | `-q` | 安静模式；无输出。 |
| `--no-interaction` | `-n` | 无交互式问题。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 详细级别。 例如，`--verbose=3`或`-vvv`显示调试详细程度，这是最详细的输出。 默认值为`--verbose=1`或`-v`。 |
| `--version` | `-V` | 显示此应用程序版本 |
| `--ansi` | 不适用 | 强制ANSI输出 |
| `--no-ansi` | 不适用 | 禁用ANSI输出 |

>[!NOTE]
>
>恭喜！您已完成快速安装。 需要更多高级帮助？ 请查看[高级安装](advanced.md)指南。
