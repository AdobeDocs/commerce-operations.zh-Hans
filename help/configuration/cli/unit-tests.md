---
title: 執行單元測試
description: 執行Adobe Commerce程式碼庫中定義的單元測試。
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 執行單元測試

{{file-system-owner}}

此命令會執行Commerce 2程式碼庫中定義的一組測試。 您可以執行所有測試或選取的測試。 每當指定了不受支援的型別時，程式就會終止並列出所有可用的型別。 執行後，詳細報告隨即顯示，其中顯示測試回合和結果。

## 必要條件

執行此命令之前，請先執行下列動作 _必須_ 為true：

- 此 `Magento_Developer` 模組必須啟用。 您可以依照以下方式啟用它：

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   使用 `--force` 選項。

- 您的系統必須設定為執行所需的測試。

例如，若要執行整合測試，您應複製 `dev/tests/integration/etc/install-config-mysql.php.dist` 至 `dev/tests/integration/etc/install-config-mysql.php` 並加以修改以符合您的環境。

## 正在執行測試

命令使用方式：

```bash
bin/magento dev:tests:run <test>
```

若要列出可用的測試型別：

```bash
bin/magento dev:tests:run --help
```

範例傳回：

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

例如，若要執行整合測試：

```bash
bin/magento dev:tests:run integration
```
