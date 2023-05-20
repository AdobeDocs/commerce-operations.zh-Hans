---
title: 命令列工具
description: 使用Commerce命令列工具執行安裝和設定工作。
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 命令列工具

Commerce有一個命令列介面(CLI)—`<magento_root>/bin/magento` — 執行安裝和設定工作，包括：

- 安裝Commerce （以及更新資料庫架構、建立部署設定等相關工作）
- 清除快取
- 管理索引，包括重新索引
- 建立翻譯字典和翻譯套件
- 為外掛程式產生不存在的類別（例如工廠和攔截器），產生物件管理員的相依性插入設定
- 部署靜態檢視檔案
- 從更少資源建立CSS

其他優點包括：

- 單一命令(`<magento_root>/bin/magento list`)列出所有可用的安裝和設定命令。
- 根據Symfony提供一致的使用者介面。
- CLI可擴充，因此協力廠商開發人員可以「插入」至其中。 這還有另一個好處，就是消除了使用者的學習曲線。
- 已停用模組的命令不顯示。

本主題說明如何使用CLI設定Adobe Commerce和Magento Open Source軟體。 如需有關安裝Commerce的資訊，請參閱 [安裝流程](../../installation/overview.md) 在 _安裝指南_.

## 必要條件

開始使用CLI之前，請確定：

1. 您的系統符合中討論的需求 [系統需求](../../installation/system-requirements.md) 在 _安裝指南_.
1. 您已完成中討論的所有先決條件任務 [必要條件](../../installation/prerequisites/overview.md) 在 _安裝指南_.
1. 登入Commerce伺服器後，切換至有權寫入Commerce檔案系統的使用者。 另請參閱 [切換到檔案系統擁有者](../../installation/prerequisites/file-system/overview.md) 在 _安裝指南_.

## 正在執行命令

對於bash shell，請使用下列語法切換到檔案系統擁有者並同時輸入命令：

```bash
su <file system owner> -s /bin/bash -c <command>
```

如果檔案系統擁有者不允許登入，您可以使用下列專案：

```bash
sudo -u <file system owner> <command>
```

**從任何目錄執行CLI命令**：

新增 `<magento_root>/bin` 至您的系統 `PATH`.

CentOS的bash shell範例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

或者，您可以執行下列作業：

- `cd <magento_root>/bin` 並以下列身分執行 `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` 是網頁伺服器docroot的子目錄
