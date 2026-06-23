---
title: 安装清漆
description: 了解Adobe Commerce缓存的Varnish安装要求。 了解安装资源和安装指南。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 0%

---

# 安装清漆

{{varnish-config-cloud}}

安装清漆超出了本指南的范围。 本主题假定受支持的Varnish版本以及在Varnish后面运行的Adobe Commerce源服务器。 本指南中的示例使用nginx作为原始Web服务器。

- [安装指南](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [清漆安装指南](https://www.varnish-cache.org/docs)
- [如何安装Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>如果要安装Vmods模块(vmod)（如saint模式），则应通过编译代码来安装Varnish，而不是通过包进行安装。 有关详细信息，请参阅[Saint模式](config-varnish-advanced.md#saint-mode)。

## 确认您的清漆版本

打开终端并输入以下命令以显示Varnish版本：

```shell
varnishd -V
```

在继续之前，请确保[Adobe Commerce支持](../../installation/system-requirements.md)已安装的Varnish版本。 如果您运行的是不支持的版本，则必须升级到支持的版本。 有关更多信息，请参阅Varnish安装文档。
