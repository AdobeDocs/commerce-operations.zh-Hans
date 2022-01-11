---
title: 升级兼容性工具先决条件
description: '验证您的系统是否满足为您的Adobe Commerce项目运行升级兼容性工具所需的要求。 '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 升级兼容性工具先决条件

运行升级兼容性工具可帮助您确定必须执行的操作 **之前** 升级Adobe Commerce版本。

运行升级兼容性工具的最低要求是：

| **要求** | **约束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 编辑器 | 无 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`或 `>=16.0.0`) |
| 内存限制 | 至少2GB RAM |
| Adobe Commerce Access密钥 | 无 |
| Adobe Commerce（开源或企业版） | 无 |

您可以在任何操作系统中运行升级兼容性工具。 无需运行Adobe Commerce实例所在的升级兼容性工具。

升级兼容性工具必须能够访问Adobe Commerce实例的源代码。 例如，您可以在一台服务器上安装它，并将其指向另一台服务器上的Adobe Commerce安装。 请参阅 [安装](../upgrade-compatibility-tool/install.md) 主题以了解更多信息。
