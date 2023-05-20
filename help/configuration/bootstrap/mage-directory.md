---
title: 自訂基底目錄路徑
description: 使用MAGE_DIRS變數來設定絕對路徑的陣列。
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# 基底目錄路徑

此 `MAGE_DIRS` 環境變數可讓您指定自訂基本目錄路徑和基本URL的片段，商務應用程式會使用這些路徑建立各種檔案的絕對路徑或產生URL。

## 設定MAGE_DIRS

指定索引鍵為常數的關聯陣列 [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] 和值分別是目錄的絕對路徑或其URL路徑。

您可以設定 `MAGE_DIRS` 下列任一種方式：

- [設定啟動程式引數的值](../bootstrap/set-parameters.md)
- 使用自訂進入點指令碼，如下所示：

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\App\Bootstrap;
   use Magento\Framework\App\Filesystem\DirectoryList;
   use Magento\Framework\App\Http;
   
   require __DIR__ . '/app/bootstrap.php';
   $params = $_SERVER;
   $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
        DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
        DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
        DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
        DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
        DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
   ];
   $bootstrap = Bootstrap::create(BP, $params);
   /** @var Http $app */
   $app = $bootstrap->createApplication(Http::class);
   $bootstrap->run($app);
   ```

上述範例會設定 `[cache]` 和 `[media]` 目錄 `/mnt/nfs/cache` 和 `/mnt/nfs/media`（分別）。

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
