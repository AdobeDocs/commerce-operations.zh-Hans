---
title: 开发系统设置
description: 了解如何为Commerce应用程序设置开发系统。
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%
---
# 开发系统设置

您可以拥有任意数量的开发系统，但前提是以下条件适用于所有系统：

- 它们都运行Commerce 2.2或更高版本
- 所有Commerce代码都在与构建和生产系统相同的存储库中受源代码控制
- 每个开发系统应使用[默认模式](../bootstrap/application-modes.md#default-mode)或[开发人员模式](../bootstrap/application-modes.md#developer-mode)
- 它具有文件系统所有权和权限集，如[开发、生成和生产系统的先决条件](../deployment/technical-details.md)中所述。
- 确保从源代码管理中排除以下所有&#x200B;_项_：

  - `vendor`目录（和子目录）
  - `generated`目录（和子目录）
  - `pub/static`目录（和子目录）
  - `app/etc/env.php`文件

- 确保`app/etc/config.php`在源代码管理中&#x200B;_包含_

如果您使用Git，`.gitignore`文件将提供前面的大部分内容。 查看[`.gitignore`引用](../reference/config-reference-gitignore.md)。
