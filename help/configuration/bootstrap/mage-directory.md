---
title: 自定义基目录路径
description: 使用MAGE_DIRS变量设置绝对路径数组。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# 基目录路径

的 `MAGE_DIRS` 环境变量允许您指定商务应用程序用来构建各种文件或生成URL的绝对路径的自定义基目录路径和基本URL片段。

## 设置MAGE_DIRS

指定关联数组，其中键是 [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] 和值分别是目录或其URL路径的绝对路径。

您可以设置 `MAGE_DIRS` 以下任何方式：

- [设置引导参数的值](../bootstrap/set-parameters.md)
- 使用以下自定义入口点脚本：

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

上面的示例为 `[cache]` 和 `[media]` 目录 `/mnt/nfs/cache` 和 `/mnt/nfs/media`，分别为。

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
