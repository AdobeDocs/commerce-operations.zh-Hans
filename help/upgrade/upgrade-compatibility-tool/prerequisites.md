---
title: '"[!DNL Upgrade Compatibility Tool] 先决条件”'
description: '验证您的系统是否满足运行 [!DNL Upgrade Compatibility Tool] 为您的Adobe Commerce项目。 '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 先决条件

{{commerce-only}}

运行 [!DNL Upgrade Compatibility Tool] 为：

| **要求** | **约束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 编辑器 | 无 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`或 `>=16.0.0`) |
| 内存限制 | 至少2GB RAM |
| Adobe Commerce Access密钥 | 无 |
| Adobe Commerce | 无 |

您可以运行 [!DNL Upgrade Compatibility Tool] （不支持Windows）。 您不必运行 [!DNL Upgrade Compatibility Tool] Adobe Commerce实例所在的位置。

对于 [!DNL Upgrade Compatibility Tool] 以访问Adobe Commerce实例的源代码。 例如，您可以在一台服务器上安装它，并将其指向另一台服务器上的Adobe Commerce安装。 请参阅 [安装](../upgrade-compatibility-tool/install.md) 主题以了解更多信息。

如果您运行的是 [!DNL Upgrade Compatibility Tool] 对于具有大模块和文件的Adobe Commerce实例，该工具可能需要大量RAM（至少2 GB）。 您可以使用 `[=MODULE-PATH]` 命令中用于指定模块路径目录的选项，以避免由于内存不足而出现的问题：

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

其中参数如下所示：

- `<dir>`:Adobe Commerce安装目录。
- `[=MODULE-PATH]`:特定模块路径目录。
