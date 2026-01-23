---
title: 升级模块和扩展
description: 使用命令行界面和编辑器升级Adobe Commerce模块和扩展。
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 升级模块和扩展

要更新或升级模块或扩展，请执行以下操作：

1. 从Marketplace或其他扩展开发人员下载更新的文件。 记下模块名称和版本。

1. 将内容导出到Adobe Commerce根安装目录。

1. 如果模块存在编辑器包，请运行以下任一操作。

   每个模块名称更新：

   ```bash
   composer update vendor/module-name
   ```

   每个版本更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 运行以下命令以升级、部署和清理缓存。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## 供应商捆绑扩展(VBE)

Adobe在2.4.4中删除了所有[VBE](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/modules/upgrade)。供应商将继续在Adobe Commerce Marketplace上支持这些扩展。

如果要继续在Adobe Commerce 2.4.4及更高版本中使用这些扩展，则必须在`composer.json`升级到2.4.4之前，更新&#x200B;_文件_&#x200B;中相应的包依赖项。有关要使用的包名称和版本，请与供应商联系。

有关更多信息，请参阅以下Adobe Commerce Marketplace列表：

- [Amazon支付](https://commercemarketplace.adobe.com//amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://commercemarketplace.adobe.com//dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://commercemarketplace.adobe.com//klarna-m2-klarna.html)
- [顶点](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html)
- [Yotpo](https://commercemarketplace.adobe.com//yotpo-module-yotpo.html)
