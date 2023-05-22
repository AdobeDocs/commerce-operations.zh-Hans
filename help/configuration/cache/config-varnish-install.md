---
title: 安裝清漆
description: 請參閱安裝光澤漆的建議。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 安裝清漆

安裝Varnish軟體不屬於本指南的範圍。 如需安裝Varnish的詳細資訊，請參閱：

- [安裝指南](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [清漆安裝指南](https://www.varnish-cache.org/docs)
- [如何安裝清漆(Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>本主題是為CentOS和Apache 2.4上的Varnish所撰寫。如果您在不同的環境中設定Varnish，有些指令可能會不同。 如需詳細資訊，請參閱上述檔案。
>
>如果您想要安裝Varnish模組(vmod) （例如saint模式），您應該編譯程式碼來安裝Varnish，而不是從套件進行安裝。 另請參閱 [Saint模式](config-varnish-advanced.md#saint-mode) 以取得更多詳細資料。

## 確認您的清漆版本

開啟終端機，然後輸入以下命令以顯示清漆版本：

```bash
varnishd -V
```

範例如下：

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

繼續之前，請確認版本為6.x。 如果您執行版本低於6.x，則必須升級至支援的版本。 如需詳細資訊，請參閱Varnish安裝檔案。
