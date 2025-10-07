---
title: 开发环境建议
description: 了解Adobe Commerce中的开发环境建议。 了解实施指导和优化策略。
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 开发环境建议

本页提供了有关Commerce开发环境的建议。

## 清理缓存而不是禁用

许多开发人员倾向于在其开发人员实例上禁用所有缓存。 我们建议只清理缓存，而不禁用所有缓存。 当您[!DNL Commerce]清理缓存[而不是完全禁用它们时，](../configuration/cli/manage-cache.md#clean-and-flush-cache-types)运行效率更高。 大多数类型的缓存在开发过程中很少失效。

如果您[禁用缓存](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)，我们建议仅在开发实例中禁用页面和块缓存。 切记在测试期间启用所有缓存。

## 在开发模式下要避免的命令

在开发模式下，请勿运行用于编译、代码生成和静态内容部署的命令。 这些命令仅构建用于生产模式。

**不要在开发模式下运行**&#x200B;生产命令：

* `setup:di:compile`生成自动生成类和优化配置缓存。

  ```bash
  bin/magento setup:di:compile
  ```

  在开发模式下，Magento会按需执行生成；您无需运行它。 如果您修改了类的签名并且需要重新生成其自动生成的`factories/proxies/interceptors`，请删除这些类或&#x200B;_生成的_&#x200B;文件夹。

* `setup:static-content:deploy`为存储部署静态内容。

  ```bash
  bin/magento setup:static-content:deploy
  ```

  在开发模式下，Magento会按需执行；您无需运行它。

## 虚拟机上的正常页面加载时间

如果您在虚拟机上进行开发，并且加载Magento页面所需的时间超过2秒，请检查您的环境设置。
