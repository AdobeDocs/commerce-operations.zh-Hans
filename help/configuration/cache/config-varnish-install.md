---
title: 安装清漆
description: 请参阅有关安装Varnish的建议。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 安装清漆

安装Varnish软件超出了本指南的范围。 有关安装Varnish的详细信息，请参阅：

- [安装指南](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [清漆安装指南](https://www.varnish-cache.org/docs)
- [如何安装Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>本主题为CentOS和Apache 2.4上的Varnish编写。如果您在不同的环境中设置Varnish，则某些命令可能不同。 有关更多信息，请参阅上述文档。
>
>如果要安装Vmods模块(vmod)（如saint模式），则应通过编译代码来安装Varnish，而不是从包进行安装。 参见 [Saint模式](config-varnish-advanced.md#saint-mode) 了解更多详细信息。

## 确认您的清漆版本

打开终端并输入以下命令以显示Varnish版本：

```bash
varnishd -V
```

下面是一个示例：

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

在继续之前，请确保版本为6.x。 如果运行版本低于6.x，则必须升级到支持的版本。 有关更多信息，请参阅Varnish安装文档。
