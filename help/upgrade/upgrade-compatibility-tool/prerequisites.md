---
title: '"[!DNL Upgrade Compatibility Tool] 先决条件”'
description: '验证您的系统是否满足运行 [!DNL Upgrade Compatibility Tool] 为您的Adobe Commerce项目。 '
source-git-commit: c4769b555df49ed2f0b2fffbeaf458c5a64816ba
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 先决条件

{{commerce-only}}

运行 [!DNL Upgrade Compatibility Tool] 帮助您确定必须执行的操作 **之前** 升级Adobe Commerce版本。

运行 [!DNL Upgrade Compatibility Tool] 为：

| **要求** | **约束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 编辑器 | 无 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`或 `>=16.0.0`) |
| 内存限制 | 至少2GB RAM |
| Adobe Commerce Access密钥 | 无 |
| Adobe Commerce | 无 |

您可以运行 [!DNL Upgrade Compatibility Tool] 在任何操作系统中。 无需运行 [!DNL Upgrade Compatibility Tool] Adobe Commerce实例所在的位置。

对于 [!DNL Upgrade Compatibility Tool] 以访问Adobe Commerce实例的源代码。 例如，您可以在一台服务器上安装它，并将其指向另一台服务器上的Adobe Commerce安装。 请参阅 [安装](../upgrade-compatibility-tool/install.md) 主题以了解更多信息。

如果您运行的是 [!DNL Upgrade Compatibility Tool] 对于具有大模块和文件的Adobe Commerce实例，该工具可能需要大量RAM，至少2GB RAM。
