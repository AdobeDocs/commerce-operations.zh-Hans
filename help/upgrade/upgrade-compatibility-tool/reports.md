---
title: '"[!DNL Upgrade Compatibility Tool] 报告”'
description: 按照以下步骤运行 [!DNL Upgrade Compatibility Tool] 在您的Adobe Commerce项目上。
source-git-commit: 1ce02c3215b01f64e86383938a257514f0e4257c
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# 报告

{{commerce-only}}

由于分析结果， [!DNL Upgrade Compatibility Tool] 可以导出包含每个文件问题列表的报表，以指定其严重性、错误代码和错误描述。 的 [!DNL Upgrade Compatibility Tool] 将报表导出为两种不同的格式：

- A [JSON文件](reports.md#json-file).
- 安 [HTML报表](reports.md#html-report).

请参阅以下报表的命令行界面示例：

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

检查 [错误消息引用](../upgrade-compatibility-tool/error-messages.md) 主题以了解有关此报表可能产生的不同错误的详细信息。

此报表还包含一个详细的摘要，其中显示：

- *当前版本*:当前安装的版本。
- *Target版本*:要升级到的版本。
- *执行时间*:分析构建报表所花费的时间(mm:ss)。
- *需要更新的模块*:包含兼容性问题和需要更新的模块的百分比。
- *需要更新的文件*:包含兼容性问题和需要更新的文件的百分比。
- *严重错误总数*:发现的严重错误数。
- *错误总数*:找到的错误数。
- *警告总数*:找到的警告数。
- *内存峰值使用率*:最大内存量 [!DNL Upgrade Compatibility Tool] 已在执行期间到达。

请参阅以下命令行界面示例：

```terminal
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## JSON文件

运行 [!DNL Upgrade Compatibility Tool] 命令行界面。 的 `JSON` 文件包含的信息与 [!DNL Upgrade Compatibility Tool] 输出：

- 已识别问题的列表。
- 分析摘要。

对于每个遇到的问题，报表会提供详细信息，如问题的严重性和描述。

要导出此 `JSON` 文件到其他输出文件夹中：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

其中参数如下所示：

- `<dir>`:Adobe Commerce安装目录。
- `[=JSON-OUTPUT-PATH]`:导出的路径目录 `JSON` 输出文件。

>[!NOTE]
>
> 输出文件夹的默认路径为 `var/output/[TIME]-results.json`.

## HTML报表

在命令行界面上运行该工具时，或通过 [!DNL Site-Wide Analysis Tool]. HTML报表还包含：

- 已识别问题的列表。
- 分析摘要。

![HTML报表 — 摘要](../../assets/upgrade-guide/uct-html-summary.png)

在 [!DNL Upgrade Compatibility Tool] 分析。

您可以根据最小问题级别过滤报表中显示的问题(默认值为 `WARNING`)。

右上角有一个下拉菜单，允许您选择其他级别。 已识别问题的列表会相应地进行过滤。

![HTML报表 — 下拉列表使用情况](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 问题级别较低的问题已去除，但您收到了通知，以便您始终了解每个模块已识别的问题。

HTML报表还包含四个不同的图表：

- **按问题严重性划分的模块**:显示按模块划分的严重性分布。
- **按问题严重性列出的文件**:按文件显示严重性分布。
- **按问题总数排序的模块**:显示10个受损最多的模块，其中考虑了警告、错误和严重错误。
- **具有相对大小和问题的模块**:模块包含的文件越多，其圆圈就越大。 模块遇到的问题越多，其圆就越红。

通过这些图表，您可以识别最易损害的模块，以及执行升级需要更多工作的模块。

![HTML报表 — 图](../../assets/upgrade-guide/uct-html-diagrams.png)

HTML报表图也会相应地更新，但 `Modules with relative sizes and issues`，通过 `min-issue-level` 那是最初设置的。

如果您想要查看 `Modules with relative sizes and issues` 图中，必须重新运行为 `--min-issue-level` 选项。

![HTML报表 — 泡泡图图](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

要将此HTML报表导出到其他输出文件夹，请执行以下操作：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

其中参数如下所示：

- `<dir>`:{{site.data.var.ee}}安装目录。
- `[=HTML-OUTPUT-PATH]`:导出的路径目录 `.html` 输出文件。

>[!NOTE]
>
> 输出文件夹的默认路径为 `var/output/[TIME]-results.html`.
