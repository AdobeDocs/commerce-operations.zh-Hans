---
title: 迁移更改
description: 了解如何使用 [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 迁移更改

增量迁移工具会安装deltalog表（带前缀） `m2_cl_*`)和触发器(用于跟踪Magento1数据库中的更改) [数据迁移](data.md). 这些delog表和触发器对于确保自上次迁移Magento以来仅迁移在迁移1中所做的更改至关重要。 这些更改包括：

* 客户通过 [店面](https://glossary.magento.com/storefront) （创建订单、审核和客户配置文件的更改）

* 所有包含订单、产品和类别的操作 [管理员](https://glossary.magento.com/magento-admin) 面板

>[!NOTE]
>
>通过管理员输入的所有其他新实体或更新实体（如属性或CMS页面）都不会包含在增量迁移中，也不会迁移。


在开始之前，请采取以下步骤进行准备：

1. 以下身份登录到应用程序服务器： [文件系统所有者](../../../installation/prerequisites/file-system/overview.md).
1. 更改为 `/bin` 目录，或确保将其添加到系统中 `PATH`.

请参阅 [首要步骤](overview.md#first-steps) 部分以了解更多详细信息。

## 运行增量迁移命令

要开始迁移增量更改，请运行：

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是从头开始迁移的可选参数。 您可以使用此参数测试迁移。

* `[-a|--auto]` 是一个可选参数，可阻止迁移在遇到完整性检查错误时停止。

* `{<path to config.xml>}` 是 `config.xml`;此参数是必需的。

>[!NOTE]
>
>增量迁移是一个连续的过程；每5秒自动重新启动一次。 使用CTRL-C中止迁移过程。


## 迁移由第三方扩展创建的数据

在 `Delta` 模式， [!DNL Data Migration Tool] 迁移仅由Magento自己的模块创建的数据，并且不负责由第三方开发人员创建的代码或扩展。 如果这些扩展在storefront数据库中创建了数据，并且商户希望在Magento2（配置文件）中包含此数据 [!DNL Data Migration Tool] 应创建并相应地修改。

如果 [扩展](https://glossary.magento.com/extension) 具有自己的表，您需要跟踪其对增量迁移的更改，请执行以下步骤：

1. 将要跟踪的表添加到 `deltalog.xml` 文件
1. 创建一个附加的增量类，该增量类将 `Migration\App\Step\AbstractDelta`
1. 将新创建类的名称添加到的增量模式部分 `config.xml`
