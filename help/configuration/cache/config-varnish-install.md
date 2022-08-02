---
title: 安装清漆
description: 请参阅有关安装清漆的建议。
source-git-commit: 688db9fcc9cd196d1560e49719b03ef32d13870d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# 安装清漆

安装清漆软件超出本指南的范围。 有关安装清漆的详细信息，请参阅：

- [安装维基](http://wiki.mikejung.biz/Varnish)
- [清漆安装导向件](https://www.varnish-cache.org/docs)
- [如何安装清漆(Tecmint)](http://www.tecmint.com/install-varnish-cache-web-accelerator)

>[!INFO]
>
>本主题是为CentOS和Apache 2.4上的清漆编写的。如果您在其他环境中设置清漆，则某些命令可能会有所不同。 有关更多信息，请参阅上面的文档。
>
>如果要安装清漆模块(vmod)（如saint模式），则应通过编译代码来安装清漆，而不是从包中安装。 请参阅 [Saint模式](config-varnish-advanced.md#saint-mode) 以了解更多详细信息。

## 确认清漆版本

打开终端并输入以下命令以显示清漆版本：

```bash
varnishd -V
```

示例如下：

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

确保版本为6.x，然后再继续。 如果您运行的版本低于6.x，则必须升级到支持的版本。 有关详细信息，请参阅清漆安装文档。
