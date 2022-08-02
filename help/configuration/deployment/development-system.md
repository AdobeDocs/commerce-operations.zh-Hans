---
title: 开发系统设置
description: 了解如何为商务应用程序设置开发系统。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# 开发系统设置

如果所有开发系统均符合以下条件，则您可以拥有任意数量的开发系统：

- 它们都运行Commerce 2.2或更高版本
- 所有商务代码在与生成系统和生产系统相同的存储库中受源代码控制
- 每个开发系统应使用 [默认模式](../bootstrap/application-modes.md#default-mode) 或 [开发人员模式](../bootstrap/application-modes.md#developer-mode)
- 它具有文件系统所有权和权限集，如 [开发、构建和生产系统的先决条件](../deployment/technical-details.md).
- 确保以下所有内容均 _排除_ 从源代码控件：

   - `vendor` 目录（和子目录）
   - `generated` 目录（和子目录）
   - `pub/static` 目录（和子目录）
   - `app/etc/env.php` 文件

- 确保 `app/etc/config.php` is _包含_ 在源控件中

如果您使用Git，则 `.gitignore` 文件提供了上述大多数内容。 请参阅 [`.gitignore` 参考](../reference/config-reference-gitignore.md).
