---
title: 开发环境Recommendations
description: 了解关于设置本地Adobe Commerce开发环境的性能建议。
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# 开发环境建议

本页提供了有关Commerce开发环境的建议。

## 清理缓存而不是禁用

许多开发人员倾向于在其开发人员实例上禁用所有缓存。 我们建议只清理缓存，而不禁用所有缓存。 [!DNL Commerce] 在以下情况下运行效率更高 [清理缓存](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) 而不是完全禁用它们。 大多数类型的缓存在开发过程中很少失效。

如果您 [禁用缓存](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)，我们建议仅在开发实例中禁用页面缓存和块缓存。 切记在测试期间启用所有缓存。

## 在开发模式下要避免的命令

在开发模式下，请勿运行用于编译、代码生成和静态内容部署的命令。 这些命令仅构建用于生产模式。

**不要运行** 开发模式下的生产命令：

* `setup:di:compile` 生成自动生成类和优化配置缓存。

  ```bash
  bin/magento setup:di:compile
  ```

  在开发模式下，Magento会按需执行生成；您无需运行生成。 如果修改了类的签名并需要重新生成其自动生成的签名 `factories/proxies/interceptors`，删除这些类或 _已生成_ 文件夹。

* `setup:static-content:deploy` 为存储部署静态内容。

  ```bash
  bin/magento setup:static-content:deploy
  ```

  在开发模式下，Magento可按需执行操作；您无需运行它。

## 虚拟机上的正常页面加载时间

如果您在VM上进行开发，并且加载Magento页面需要超过2秒的时间，请查看环境设置。
