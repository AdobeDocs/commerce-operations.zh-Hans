---
title: 安装清漆
description: 请参阅有关安装清漆的建议。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# 安装清漆

安装Varnish软件超出了本指南的范围。 有关安装Varnish的详细信息，请参阅：

- [安装指南](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [清漆安装指南](https://www.varnish-cache.org/docs)
- [如何安装清漆(Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>本主题为CentOS和Apache 2.4上的Varnish编写。如果在不同的环境中设置Varnish，则某些命令可能会不同。 有关更多信息，请参阅之前的文档。
>
>如果要安装Vmods模块(vmod)（如saint模式），则应通过编译代码来安装Varnish，而不是通过包进行安装。 有关详细信息，请参阅[Saint模式](config-varnish-advanced.md#saint-mode)。

## 确认您的清漆版本

打开终端并输入以下命令以显示Varnish版本：

```bash
varnishd -V
```

在继续之前，请确保[Adobe Commerce支持](../../installation/system-requirements.md)已安装的Varnish版本。 如果您运行的是不支持的版本，则必须升级到支持的版本。 有关更多信息，请参阅Varnish安装文档。
