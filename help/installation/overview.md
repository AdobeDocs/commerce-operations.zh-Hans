---
title: 内部部署安装概述
description: 了解 Adobe Commerce 内部部署的安装过程。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 7cc77a204d2a3c0773e6a0ab60e57e6e35f12091
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 3%

---


# 内部部署安装概述

本页概述了如何在您自己的基础架构上安装Adobe Commerce。 安装过程包括设置服务器环境、获取必要的软件和凭据以及运行安装命令。

您可以在大约30到60分钟内安装Adobe Commerce软件。 但是，在安装之前设置服务器环境所需的时间因您的经验以及您选择的技术而异。

>[!TIP]
>
>要成功继续，您应该具有中级技术知识和服务器访问权限。

安装程序将创建一个功能齐全的Adobe Commerce商店，该商店具有面向客户的店面[和](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/storefront/storefront)管理面板[。 ](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/admin/admin)在开始该过程之前，必须准备好数据库凭据、域信息和验证密钥。

## 工作流

下图说明了为内部部署环境安装Adobe Commerce时涉及的主要步骤：

![安装的工作原理](../assets/installation/on-premises-install.drawio.svg)

### 设置服务器环境

根据[先决条件](prerequisites/overview.md)安装和配置PHP、Web服务器、数据库和搜索引擎。

### 获取身份验证密钥

从Commerce Marketplace生成新的[身份验证密钥](prerequisites/authentication-keys.md)（或复制现有密钥）以访问Adobe Commerce Composer包。

### 获取Adobe Commerce软件

使用[编辑器](prerequisites/commerce.md)（推荐）或从GitHub克隆下载以进行开发贡献。

如果要向Magento Open Source代码库贡献内容或自定义应用程序，请[克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存储库。 此方法需要同时熟悉GitHub和Composer。

### 安装应用程序

使用特定配置运行安装命令。 有关完整示例，请参阅[快速入门](composer.md)。

>[!NOTE]
>
>如果由于必备软件未正确设置而使步骤失败，请查看[必备项](prerequisites/overview.md)。

### 验证安装

[测试](next-steps/verify.md)您的店面和管理面板，确保一切正常运行。

## 常见安装问题

- **权限错误**：确保文件系统拥有权和权限正确
- **数据库连接失败**：验证数据库凭据和网络连接
- **身份验证密钥错误**：确认您的Commerce Marketplace密钥有效且有效
- **内存限制**：确保分配足够的PHP内存（建议最小2GB）
