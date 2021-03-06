---
title: 开发环境Recommendations
description: 了解有关设置本地Adobe Commerce或Magento Open Source开发环境的性能建议。
source-git-commit: 87b353b408ecd7f55cea5b4775a0c8523952abc0
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# 开发环境建议

本页为商务开发环境提供了建议。

## 清理缓存，而不是禁用

许多开发人员倾向于禁用其开发人员实例上的所有缓存。 我们建议只清除缓存，而不禁用所有缓存。 [!DNL Commerce] 运行效率更高 [清理缓存] 而不是完全禁用它们。 大多数类型的缓存在开发过程中很少失效。

如果您 [禁用缓存]，我们建议仅在开发实例中禁用页面缓存和阻止缓存。 请记住在测试期间启用所有缓存。

## 在开发模式中避免的命令

在开发模式下，请勿运行用于编译、代码生成和静态内容部署的命令。 这些命令的构建仅供在生产模式下使用。

**不运行** 开发模式下的生产命令：

* `setup:di:compile` 生成自动生成的类和优化的配置缓存。

   ```bash
   bin/magento setup:di:compile
   ```

   在开发模式下，Magento按需生成；您无需运行它。 如果修改了类的签名，并且需要重新生成其自动生成的签名 `factories/proxies/interceptors`，删除这些类或 _生成_ 文件夹。

* `setup:static-content:deploy` 为存储部署静态内容。

   ```bash
   bin/magento setup:static-content:deploy
   ```

   在开发模式下，Magento按需执行；您无需运行它。

## 虚拟机上的正常页面加载时间

如果您在VM上进行开发，并且加载Magento页面需要超过2秒的时间，请查看环境设置。

<!-- Link definitions -->

[清理缓存]: https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cache.html#config-cli-subcommands-cache-clean
[禁用缓存]: https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cache.html#config-cli-subcommands-cache-en
