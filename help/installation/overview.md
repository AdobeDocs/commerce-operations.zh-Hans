---
title: 内部部署安装概述
description: 了解 Adobe Commerce 内部部署的安装过程。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# 内部部署安装概述

>[!NOTE]
>
>下图提供了Adobe Commerce的&#x200B;_&#x200B;**内部部署**&#x200B;_&#x200B;安装的高级概述：

![安装的工作原理](../assets/installation/install-diagram-24.svg)

一般安装流程如下所示：

1. 设置服务器环境。

   安装必备的软件，包括PHP、Apache、MySQL和搜索引擎。 有关详细信息，请参阅[系统要求](system-requirements.md)。

1. 将[身份验证密钥](prerequisites/authentication-keys.md)获取到Commerce Composer存储库。

1. 获取Adobe Commerce软件。

   * （推荐）获取[Composer中继](composer.md)以管理模块及其依赖项。

   * 如果要参与Magento Open Source代码库或自定义应用程序，请[克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存储库。 此方法需要同时熟悉GitHub和Composer。

1. 使用命令行安装应用程序。

   如果步骤因必备软件未正确设置而失败，请查看[必备项](prerequisites/overview.md)。

1. [通过查看您的店面和管理员来验证](next-steps/verify.md)安装。
