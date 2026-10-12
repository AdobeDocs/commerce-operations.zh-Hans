---
title: 自定义基目录路径
description: 使用MAGE_DIRS变量可设置绝对路径数组。
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%
---
# 基本目录路径

`MAGE_DIRS`环境变量允许您指定自定义基本目录路径和基本URL的片段，Commerce应用程序使用这些路径构建各种文件的绝对路径或生成URL。

## 设置MAGE_DIRS

指定一个关联数组，其中键是来自[\\Magento\\App\\Filesystem\\DirectoryList](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php)的常量，值分别为目录的绝对路径或其URL路径。

您可以通过以下任意方式设置`MAGE_DIRS`：

- [设置引导参数值](../bootstrap/set-parameters.md)
- 使用自定义入口点脚本，如下所示：

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
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

上述示例分别将`[cache]`和`[media]`目录的路径设置为`/mnt/nfs/cache`和`/mnt/nfs/media`。

