---
title: 内部部署安装概述
description: 了解Adobe Commerce内部部署的安装过程。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 内部部署安装概述

>[!NOTE]
>
>下图简要概述了 _**内部部署**_ Adobe Commerce的安装：

![安装工作原理](../assets/installation/install-diagram-24.svg)

一般安装流程如下所示：

1. 设置服务器环境。

   安装必备的软件，包括PHP、Apache、MySQL和搜索引擎。 请参阅 [系统要求](system-requirements.md) 以了解更多信息。

1. Get [身份验证密钥](prerequisites/authentication-keys.md) 到Commerce Composer存储库。

1. 获取Adobe Commerce或Magento Open Source软件。

   * （推荐）获取 [Composer中继包](composer.md) 管理模块及其依赖关系。

   * 如果要向Magento Open Source代码库贡献内容或自定义应用程序， [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存储库。 此方法需要同时熟悉GitHub和Composer。

1. 使用命令行安装应用程序。

   如果由于必备软件未正确设置而导致步骤失败，请查看 [先决条件](prerequisites/overview.md).

1. [验证](next-steps/verify.md) 通过查看您的店面和管理员进行安装。
