---
title: 迁移概述
description: 了解如何使用 [!DNL Data Migration Tool]开始将数据从Magento1迁移到Magento2。
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 迁移概述

在开始迁移之前，请停止所有Magento1 cron作业。

在迁移过程中，请遵循以下一般规则以成功迁移：

1. **不要**&#x200B;在Magento1管理员中进行更改，但订单管理（发运、创建发票和贷项通知单）除外
1. **不**&#x200B;更改任何代码
1. **不要**&#x200B;在Magento2管理员和店面中进行更改

>[!TIP]
>
>允许在Magento1店面中进行所有操作。

## 运行[!DNL Data Migration Tool]

此部分说明如何运行[!DNL Data Migration Tool]以迁移设置、数据或增量更改。

### 首要步骤

1. 以具有写入文件系统权限的用户身份登录或切换到应用程序服务器。 请参阅[切换到文件系统所有者](../../../installation/prerequisites/file-system/overview.md)。

   如果使用bash shell，则可以使用以下语法切换到文件系统所有者并同时输入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果文件系统所有者不允许登录，您可以执行以下操作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 若要从任何目录运行Magento命令，请将`<magento_root>/bin`添加到您的系统`PATH`。

   由于外壳的语法不同，请查阅[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)之类的引用。

   CentOS的bash shell示例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   或者，也可以通过以下方式运行命令：

   - `cd <magento_root>/bin`并作为`./magento <command name>`运行
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>`是Web服务器docroot的子目录。

### 命令语法

以下是典型的命令示例：

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

- `<mode>`可以是：[`settings`](settings.md)、[`data`](data.md)或[`delta`](delta.md)
- `[-r|--reset]`是从头开始迁移的可选参数。 可以使用此参数测试迁移。
- `[-a|--auto]`是一个可选参数，当遇到完整性检查错误时，它可阻止停止迁移。
- `{<path to config.xml>}`是`config.xml`的绝对文件系统路径；此参数是必需的。

>[!NOTE]
>
>日志将写入`<magento_root>/var/`目录。


## 迁移顺序

创建[!DNL Data Migration Tool]时，我们假定了以下数据传输顺序：

1. [设置](settings.md)
1. [数据](data.md)
1. [更改](delta.md)

我们强烈建议按相同顺序迁移数据。
