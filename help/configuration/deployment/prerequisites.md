---
title: 部署的必要條件
description: 請參閱將Commerce部署至開發、組建或生產系統的先決條件清單。
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# 開發、建置和生產系統的先決條件

開發、組建和生產系統的檔案許可權和擁有權必須保持一致。 若要讓此功能發揮作用，您必須：

- 下列所有專案：

   - 在所有系統上設定相同的檔案系統擁有者使用者名稱
   - 請確定網頁伺服器在所有系統上都以相同使用者身分執行
   - 確定檔案系統擁有者位於所有系統的網頁伺服器群組中

- 使用下列准則，視需要變更每個系統上的Commerce檔案系統許可權和擁有權：

   - 開發和建置： [設定安裝前的擁有權和許可權（兩個使用者）](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - 生產： [開發和生產中的商務擁有權和許可權](file-system-permissions.md)

>[!INFO]
>
>如果您選擇此方法，則每次從組建系統提取程式碼時，都必須設定檔案系統許可權和擁有權（若您的組建系統上的檔案系統擁有者或Web伺服器使用者不同）。
