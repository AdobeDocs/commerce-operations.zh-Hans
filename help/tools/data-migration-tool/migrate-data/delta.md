---
title: 迁移更改
description: 了解如何仅迁移自上次Magento1数据迁移以来发生更改的数据 [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# 迁移更改

增量迁移工具安装增量表（带前缀） `m2_cl_*`)和触发器（用于跟踪更改）在Magento1数据库中 [数据迁移](data.md). 要确保仅迁移自上次迁移数据以来在Magento1中所做的更改，这些增量表和触发器至关重要。 这些更改包括：

* 客户通过店面添加的数据（创建的订单、审查和客户配置文件中的更改）

* “管理员”面板中对订单、产品和类别的所有操作

>[!NOTE]
>
>通过管理员输入的所有其他新实体或更新实体（如属性或CMS页面）不会包含在增量迁移中，也不会进行迁移。


在开始之前，请执行以下步骤进行准备：

1. 以以下身份登录到应用程序服务器 [文件系统所有者](../../../installation/prerequisites/file-system/overview.md).
1. 更改为 `/bin` 目录，或确保将其添加到系统中 `PATH`.

请参阅 [首要步骤](overview.md#first-steps) 部分以了解更多详细信息。

## 运行增量迁移命令

要开始迁移增量更改，请运行：

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是一个可选参数，可从头开始迁移。 可以使用此参数测试迁移。

* `[-a|--auto]` 是一个可选参数，可防止在遇到完整性检查错误时停止迁移。

* `{<path to config.xml>}` 是绝对的文件系统路径 `config.xml`；此参数是必需的。

>[!NOTE]
>
>增量迁移是一个连续的过程；每5秒自动重新启动一次。 使用CTRL-C中止迁移过程。


## 迁移由第三方扩展创建的数据

在 `Delta` 模式， [!DNL Data Migration Tool] 仅迁移由Magento自己的模块创建的数据，对第三方开发人员创建的代码或扩展不负责。 如果这些扩展在店面数据库中创建了数据，并且商家希望在Magento2中拥有这些数据 — 的配置文件 [!DNL Data Migration Tool] 应相应地创建和修改。

如果扩展有自己的表，并且您需要跟踪其对增量迁移所做的更改，请执行以下步骤：

1. 将要跟踪的表添加到 `deltalog.xml` 文件
1. 创建一个额外的delta类，以扩展 `Migration\App\Step\AbstractDelta`
1. 将新创建的类的名称添加到的delta模式部分 `config.xml`
