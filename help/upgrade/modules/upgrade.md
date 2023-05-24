---
title: 升级模块和扩展
description: 使用命令行界面和编辑器升级Adobe Commerce和Magento Open Source模块及扩展。
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 升级模块和扩展

要更新或升级模块或扩展，请执行以下操作：

1. 从Marketplace或其他扩展开发人员下载更新的文件。 记下模块名称和版本。

1. 将内容导出到Adobe Commerce或Magento Open Source根安装目录。

1. 如果模块存在编辑器包，请运行以下任一操作。

   按模块名称更新：

   ```bash
   composer update vendor/module-name
   ```

   每个版本更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 运行以下命令升级、部署和清理缓存。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## 供应商捆绑的扩展(VBE)

Adobe已全部删除 [VBE](https://devdocs.magento.com/extensions/vendor/) 在2.4.4中。供应商将继续在Adobe Commerce Marketplace上支持这些扩展。

如果要继续在Adobe Commerce 2.4.4及更高版本中使用这些扩展，必须在中更新相应的包依赖项。 `composer.json` 文件 _早于_ 升级到2.4.4。有关要使用的包名称和版本，请与供应商联系。

有关更多信息，请参阅以下Adobe Commerce Marketplace列表：

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [克拉尔纳](https://marketplace.magento.com/klarna-m2-klarna.html)
- [顶点](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [约特波](https://marketplace.magento.com/yotpo-module-yotpo.html)
