---
title: 示例数据概述
description: 了解如何为Adobe Commerce和Magento Open Source项目使用示例数据。
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 示例数据概述

示例数据提供基于Luma主题的店面，配备了产品、类别、客户注册等。 它的作用就像一个Commerce店面，您可以使用管理员操纵价格、库存和促销定价规则。

您可以在安装Commerce软件之前或之后安装示例数据。 使用完示例数据后，您可以将其删除或全新安装，如中所述 [删除示例数据模块或更新示例数据](remove-or-update.md).

>[!WARNING]
>
>无法卸载示例数据。 我们建议您仅使用示例数据来了解Adobe Commerce和Magento Open Source的工作原理。 避免在安装了示例数据的系统中进行任何开发。

您可以通过以下任意方式安装可选示例数据：

| 安装方法 | 描述 | 所需技能级别 |
|--- |--- |--- |
| 使用编辑器 | [运行 `magento sampledata:deploy` 修改应用程序的根目录 `composer.json`](composer-packages.md) 以启用示例数据模块。 | 需要Composer知识和对Commerce文件系统的访问权限。 |
| 克隆存储库 | [克隆GitHub存储库](git-repositories.md) 和示例数据存储库，然后将它们链接在一起。 | 仅供参与开发的开发人员使用。 其他所有人都应使用上述方法之一。 |
