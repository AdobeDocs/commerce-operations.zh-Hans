---
title: URN熒光筆
description: 瞭解如何在IDE中設定URN反白顯示。
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# URN熒光筆概述

{{file-system-owner}}

Commerce程式碼參考所有XSD結構描述為 [統一資源名稱(URN)](https://www.ietf.org/rfc/rfc2141.txt). 如果您正在開發程式碼並需要參考XSD，這個命令會設定您的整合式開發人員環境(IDE)來識別和強調URN。 如此可讓開發更輕鬆。

依預設，像PhpStorm這樣的IDE未設定為識別URN，因此它們會以紅色文字顯示，如下所示：

![PhpStorm未設定為識別URN](../../assets/configuration/urn-before.png)

此 `bin/magento dev:urn-catalog:generate` command可讓您的IDE （目前只有PhpStorm和Visual Studio Code）識別並反白下列URN：

![啟用IDE以辨識URN](../../assets/configuration/urn-after.png)

具體而言，這個指令會建立下列PhpStorm組態：

![PhpStorm設定範例](../../assets/configuration/urn-settings.png)

## 設定IDE

目前僅支援PhpStorm和Visual Studio Code。

命令語法：

```bash
bin/magento dev:urn-catalog:generate <path>
```

位置 `<path>` 是PhpStorm的路徑 `misc.xml` 檔案，此檔案位於專案根目錄的相對位置。 通常， `<path>` 是 `.idea/misc.xml`.

>[!INFO]
>
>若要讓您的「結構描述和DTD」保持最新狀態，請執行 `dev:urn-catalog:generate` command ，每次新增、修改或移除包含的Commerce 2模組時 `*.xsd` 檔案。
