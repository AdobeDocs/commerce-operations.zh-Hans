---
title: 本地安装概述
description: 了解Adobe Commerce和Magento Open Source的本地部署的安装过程。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# 本地安装概述

>[!NOTE]
>
>下图提供了 _**本地**_ Adobe Commerce和Magento Open Source的安装：

![安装工作原理](../assets/installation/install-diagram-24.svg)

一般安装流程如下：

1. 设置服务器环境。

   安装必备软件，包括PHP、Apache、MySQL和搜索引擎。 请参阅 [系统要求](system-requirements.md) 以了解更多信息。

1. 获取 [身份验证密钥](prerequisites/authentication-keys.md) 到商务编辑器存储库。

1. 获取Adobe Commerce或Magento Open Source软件。

   * （推荐）获取 [编辑器元包](composer.md) 管理模块及其依赖关系。

   * 如果要参与Magento Open Source代码库或自定义应用程序， [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存储库。 此方法需要熟悉GitHub和编辑器。

1. 使用命令行安装应用程序。

   如果由于未正确设置先决条件软件而导致步骤失败，请查看 [先决条件](prerequisites/overview.md).

1. [验证](next-steps/verify.md) 通过查看店面和管理员进行的安装。

