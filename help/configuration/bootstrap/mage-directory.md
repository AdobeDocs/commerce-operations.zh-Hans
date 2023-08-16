---
title: 自定义基目录路径
description: 使用MAGE_DIRS变量可设置绝对路径数组。
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# 基本目录路径

此 `MAGE_DIRS` 环境变量允许您指定自定义基本目录路径和基本URL片段，商务应用程序使用这些路径构建各种文件的绝对路径或生成URL。

## 设置MAGE_DIRS

指定一个关联数组，其中键是来自的常量 [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] 和值分别是目录的绝对路径或其URL路径。

您可以设置 `MAGE_DIRS` 通过下列任意方式执行：

- [设置引导参数值](../bootstrap/set-parameters.md)
- 使用自定义入口点脚本，如下所示：

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

上例为以下对象设置路径： `[cache]` 和 `[media]` 目录 `/mnt/nfs/cache` 和 `/mnt/nfs/media`、ID名称和ID名称等。

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
