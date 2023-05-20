---
title: 開發環境Recommendations
description: 瞭解設定本機Adobe Commerce或Magento Open Source開發環境的效能建議。
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 開發環境建議

此頁面提供Commerce開發環境的建議。

## 清除快取而非停用

許多開發人員傾向於在其開發人員執行個體上停用所有快取。 我們建議只清除快取，不要停用所有快取。 [!DNL Commerce] 執行效率更高，當您 [清除快取](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) 而不是完全停用。 大多數型別的快取在開發期間很少會失效。

若您 [停用快取](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)，我們建議僅在開發執行個體中停用頁面和區塊快取。 請記得在測試期間啟用所有快取。

## 在開發模式中要避免的命令

在開發模式中，請勿執行編譯、程式碼產生和靜態內容部署的命令。 這些指令僅用於生產模式。

**不要執行** 開發模式下的生產命令：

* `setup:di:compile` 產生自動產生的類別和最佳化的設定快取。

   ```bash
   bin/magento setup:di:compile
   ```

   在開發模式中，Magento會依需求執行產生；您不需要執行。 如果您修改了類別的簽章，並且需要重新產生其自動產生的 `factories/proxies/interceptors`，移除這些類別或 _已產生_ 資料夾。

* `setup:static-content:deploy` 為存放區部署靜態內容。

   ```bash
   bin/magento setup:static-content:deploy
   ```

   在開發模式中，Magento會視需要執行；您不需要執行。

## 虛擬機器器上的正常頁面載入時間

如果您在VM上進行開發，且載入Magento頁面需要超過2秒的時間，請檢閱環境設定。
