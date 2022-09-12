---
title: 示例数据概述
description: 了解如何为Adobe Commerce和Magento Open Source项目使用示例数据。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# 示例数据概述

示例数据基于Luma主题提供了一个店面，内容包括产品、类别、客户注册等。 它的功能与商业店面类似，您可以使用管理员来处理价格、库存和促销定价规则。

您可以在安装商务软件之前或之后安装示例数据。 完成采样数据后，您可以删除该数据，也可以按照 [删除示例数据模块或更新示例数据](remove-or-update.md).

>[!WARNING]
>
>无法卸载示例数据。 我们建议您仅使用示例数据来了解Adobe Commerce和Magento Open Source的工作方式。 避免在安装了示例数据的系统中进行任何开发。

您可以通过以下任一方式安装可选示例数据：

| 安装方法 | 描述 | 所需技能水平 |
|--- |--- |--- |
| 使用编辑器 | [运行 `magento sampledata:deploy` 修改应用程序的根 `composer.json`](composer-packages.md) 启用示例数据模块。 | 需要编辑器知识并有权访问商务文件系统。 |
| 克隆存储库 | [克隆GitHub存储库](git-repositories.md) 和示例数据存储库，然后将它们链接在一起。 | 仅供参与开发人员使用。 其他每个人都应使用上述方法之一。 |
