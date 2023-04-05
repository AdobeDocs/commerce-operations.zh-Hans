---
title: 迁移概述
description: 了解如何开始将数据从Magento1迁移到Magento2，使用 [!DNL Data Migration Tool].
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# 迁移概述

在开始迁移之前，请停止所有Magento1 cron作业。

在迁移过程中，请遵循以下常规规则成功迁移：

1. **不要** 在“Magento1管理员”中进行更改，但订单管理（发运、创建发票和贷项通知单）除外
1. **不要** 更改任何代码
1. **不要** 在Magento2管理员和店面中进行更改

>[!TIP]
>
>允许在Magento1店面中执行所有操作。

## 运行 [!DNL Data Migration Tool]

本节将演示如何运行 [!DNL Data Migration Tool] 迁移设置、数据或增量更改。

### 首要步骤

1. 以有权写入文件系统的用户身份登录到应用程序服务器，或切换到。 请参阅 [切换到文件系统所有者](../../../installation/prerequisites/file-system/overview.md).

   如果使用bash shell，则可以使用以下语法切换到文件系统所有者并同时输入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果文件系统所有者不允许登录，您可以执行以下操作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 要从任何目录运行Magento命令，请添加 `<magento_root>/bin` 到系统 `PATH`.

   由于壳的语法不同，因此请参考 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS的bash shell示例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   或者，您也可以通过以下方式运行命令：

   - `cd <magento_root>/bin` 以 `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` 是web服务器docroot的子目录。

### 命令语法

以下是典型的命令示例：

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

- `<mode>` 可能为： [`settings`](settings.md), [`data`](data.md)或 [`delta`](delta.md)
- `[-r|--reset]` 是从头开始迁移的可选参数。 您可以使用此参数测试迁移。
- `[-a|--auto]` 是一个可选参数，可阻止迁移在遇到完整性检查错误时停止。
- `{<path to config.xml>}` 是 `config.xml`;此参数是必需的。

>[!NOTE]
>
>日志会写入 `<magento_root>/var/` 目录访问Advertising Cloud的帮助。


## 迁移顺序

当我们创建 [!DNL Data Migration Tool]，我们假定了以下数据传输序列：

1. [设置](settings.md)
1. [数据](data.md)
1. [更改](delta.md)

我们强烈建议按相同顺序迁移数据。
