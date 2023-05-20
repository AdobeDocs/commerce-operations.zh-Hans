---
title: 模組更新失敗後回覆
description: 在遇到模組更新錯誤後，疑難排解Adobe Commerce或Magento Open Source升級。
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# 模組更新失敗後回覆

如果您的模組更新失敗，控制檯記錄中會顯示類似下列的訊息：

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

在上一個範例中，沒有要復原的元件版本。 請連絡元件廠商，或嘗試自行解決問題。

同時，您可以按一下「 」，將版本復原到先前的版本 **復原**，可復原資料，即使您先前未備份亦然。
