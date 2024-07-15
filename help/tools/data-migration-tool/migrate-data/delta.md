---
title: 迁移更改
description: 了解如何使用 [!DNL Data Migration Tool]仅迁移自上次Magento1数据迁移以来发生更改的数据。
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# 迁移更改

增量迁移工具在数据的[迁移](data.md)期间在Magento1数据库中安装deltalog表（前缀为`m2_cl_*`）和触发器（用于跟踪更改）。 要确保仅迁移自上次迁移数据以来在Magento1中所做的更改，这些增量表和触发器至关重要。 这些更改包括：

* 客户通过店面添加的数据（创建的订单、审查和客户配置文件中的更改）

* “管理员”面板中对订单、产品和类别的所有操作

>[!NOTE]
>
>通过管理员输入的所有其他新实体或更新实体（如属性或CMS页面）不会包含在增量迁移中，也不会进行迁移。


在开始之前，请执行以下步骤进行准备：

1. 以[文件系统所有者](../../../installation/prerequisites/file-system/overview.md)的身份登录到应用程序服务器。
1. 更改为`/bin`目录或确保将其添加到您的系统`PATH`。

有关更多详细信息，请参阅[首要步骤](overview.md#first-steps)部分。

## 运行增量迁移命令

要开始迁移增量更改，请运行：

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]`是从头开始迁移的可选参数。 可以使用此参数测试迁移。

* `[-a|--auto]`是一个可选参数，当遇到完整性检查错误时，它可阻止停止迁移。

* `{<path to config.xml>}`是`config.xml`的绝对文件系统路径；此参数是必需的。

>[!NOTE]
>
>增量迁移是一个连续的过程；每5秒自动重新启动一次。 使用CTRL-C中止迁移过程。


## 迁移由第三方扩展创建的数据

在`Delta`模式下，[!DNL Data Migration Tool]仅迁移由Magento自己的模块创建的数据，而不负责第三方开发人员创建的代码或扩展。 如果这些扩展在店面数据库中创建了数据，而商家希望在Magento2中存储这些数据，则应相应地创建和修改[!DNL Data Migration Tool]的配置文件。

如果扩展有自己的表，并且您需要跟踪其对增量迁移所做的更改，请执行以下步骤：

1. 将要跟踪的表添加到`deltalog.xml`文件
1. 创建扩展`Migration\App\Step\AbstractDelta`的附加delta类
1. 将新创建的类的名称添加到`config.xml`的增量模式部分
