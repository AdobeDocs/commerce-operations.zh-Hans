---
title: 生产系统设置
description: 了解如何为商务应用程序设置生产系统。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# 生产系统设置

您可以有一个生产系统。 以下所有内容必须为true:

- 所有商务代码都位于与开发和构建系统相同的存储库中的源代码控制中
- 确保以下所有内容均 _包含_ 在源代码管理中：

   - `app/etc/config.php`
   - `generated` 目录（和子目录）
   - `pub/media` 目录
   - `pub/media/wysiwyg` 目录（和子目录）
   - `pub/static` 目录（和子目录）

- 必须安装Commerce 2.2或更高版本，并为 [生产模式](../bootstrap/application-modes.md#production-mode)
- 它具有文件系统所有权和权限集，如 [开发、构建和生产系统的先决条件](../deployment/prerequisites.md).

## 设置生产机器

要设置生产计算机，请执行以下操作：

1. 安装Commerce或从源代码管理中提取它后，作为或切换到 [文件系统所有者](https://glossary.magento.com/magento-file-system-owner).
1. 创建 `~/.ssh/.composer/auth.json` 如果您尚未执行此操作，请执行以下操作。

   创建目录：

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   创建 `auth.json` 在目录中。

   `auth.json` 必须包含 [身份验证密钥](../../installation/prerequisites/authentication-keys.md).

   示例如下：

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. 将更改保存到 `auth.json`.
1. 复制 `<Commerce root dir>/app/etc/env.php` 从开发系统到生产系统。
1. 打开 `env.php` 在文本编辑器中，更改任何必需的值（例如，数据库连接信息）。
1. 运行 [`magento config:set`](../cli/set-configuration-values.md) 或 [`magento config:set-sensitive`](../cli/set-configuration-values.md) 命令分别设置任何系统特定或敏感配置值的值。

   以下部分显示一个示例。

## 在生产系统上设置配置值

本节将讨论如何使用 `magento config:sensitive:set` 命令。

要设置敏感值，请执行以下操作：

1. 查找要使用 [敏感值引用](../reference/config-reference-sens.md).
1. 请注意设置的配置路径。
1. 以文件系统所有者的身份登录到生产系统，或切换到。
1. 更改为Commerce安装目录。
1. 输入以下命令：

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   例如，将YouTube API密钥的值设置为 `1234`，输入

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   您还可以按如下方式以交互方式设置一个或多个值：

   ```bash
   bin/magento config:sensitive:set -i
   ```

   出现提示时，为每个敏感设置输入一个值，或按Enter键跳过一个值并移到下一个值。

1. 要验证是否已设置该值，请登录到管理员。
1. 在管理员中找到设置。

   例如，YouTube API密钥设置位于 **商店** >设置> **配置** > **目录** > **目录** > **产品视频**.

   设置显示在管理员中，无法编辑。 下图显示了一个示例。

   ![管理员中的敏感设置](../../assets/configuration/sensitive-set.png)
