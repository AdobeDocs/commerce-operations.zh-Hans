---
title: 生产系统设置
description: 了解如何为Commerce应用程序设置生产系统。
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 生产系统设置

您可以拥有一个生产系统。 以下所有条件都必须为true：

- 所有Commerce代码与开发和构建系统位于同一存储库中的源代码控制中
- 确保以下所有选项均可用 _已包括_ 在源代码管理中：

   - `app/etc/config.php`
   - `generated` 目录（和子目录）
   - `pub/media` 目录
   - `pub/media/wysiwyg` 目录（和子目录）
   - `pub/static` 目录（和子目录）

- 必须安装并设置Commerce 2.2或更高版本 [生产模式](../bootstrap/application-modes.md#production-mode)
- 它具有文件系统所有权和权限集，如中所述 [开发、构建和生产系统的先决条件](../deployment/prerequisites.md).

## 设置生产计算机

要设置生产计算机，请执行以下操作：

1. 安装Commerce或从源代码管理中提取它后，以文件系统所有者的身份登录生产服务器或切换到文件系统所有者。
1. 创建 `~/.ssh/.composer/auth.json` 如果你还没有这么做的话。

   创建目录：

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   创建 `auth.json` 在那个目录里。

   `auth.json` 必须包含 [身份验证密钥](../../installation/prerequisites/authentication-keys.md).

   下面是一个示例：

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
1. 打开 `env.php` 在文本编辑器中，并更改所需的任何值（例如，数据库连接信息）。
1. 运行 [`magento config:set`](../cli/set-configuration-values.md) 或 [`magento config:set-sensitive`](../cli/set-configuration-values.md) 命令，分别设置任何系统特定或敏感配置值的值。

   以下部分显示了一个示例。

## 在生产系统上设置配置值

本节讨论如何使用在您的生产系统上设置敏感值。 `magento config:sensitive:set` 命令。

要设置敏感值，请执行以下操作：

1. 使用查找要设置的值 [敏感值引用](../reference/config-reference-sens.md).
1. 记下设置的配置路径。
1. 以文件系统所有者的身份登录生产系统，或切换到文件系统所有者。
1. 转到Commerce安装目录。
1. 输入以下命令：

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   例如，将YouTube API密钥的值设置为 `1234`，输入

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   您还可以以交互方式设置一个或多个值，如下所示：

   ```bash
   bin/magento config:sensitive:set -i
   ```

   出现提示时，为每个敏感设置输入一个值，或按Enter跳过一个值并移到下一个值。

1. 要验证是否已设置该值，请登录到管理员。
1. 在“管理员”中找到设置。

   例如，YouTube API密钥设置位于 **商店** >设置> **配置** > **目录** > **目录** > **产品视频**.

   该设置显示在Admin中，无法编辑。 下图显示了一个示例。

   ![管理员中的敏感设置](../../assets/configuration/sensitive-set.png)
