---
title: ’[!DNL Upgrade Compatibility Tool] 报告
description: 按照以下步骤运行 [!DNL Upgrade Compatibility Tool] 在您的Adobe Commerce项目上。
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# 报表

{{commerce-only}}

经过分析， [!DNL Upgrade Compatibility Tool] 可以导出一个报告，其中包含每个文件的问题列表，指定其严重性、错误代码和错误说明。 此 [!DNL Upgrade Compatibility Tool] 将报告导出为两种不同的格式：

- A [JSON文件](reports.md#json-file).
- An [HTML报表](reports.md#html-report).

请参阅以下报告的命令行界面示例：

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

查看 [错误消息引用](../upgrade-compatibility-tool/error-messages.md) 主题以了解有关此报告可产生的不同错误的更多信息。

此报表还包括一个详细的摘要，其中显示：

- *当前版本*：当前安装的版本。
- *目标版本*：要升级到的版本。
- *执行时间*：分析构建报告所用的时间(mm：ss)。
- *需要更新的模块*：包含兼容性问题并需要更新的模块的百分比。
- *需要更新的文件*：包含兼容性问题并需要更新的文件的百分比。
- *严重错误总数*：找到的严重错误数。
- *错误总数*：找到的错误数。
- *警告总数*：找到的警告数。
- *内存峰值使用率*：最大内存量 [!DNL Upgrade Compatibility Tool] 在执行期间达到。

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

您可以在运行时获取JSON文件输出 [!DNL Upgrade Compatibility Tool] 在命令行界面上。 此 `JSON` 文件包含的信息与 [!DNL Upgrade Compatibility Tool] 输出：

- 已识别问题的列表。
- 分析摘要。

对于每个遇到的问题，报告都会提供详细信息，例如问题的严重性和描述。

要导出此，请执行以下操作 `JSON` 文件放入其他输出文件夹：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

其中参数如下：

- `<dir>`：Adobe Commerce安装目录。
- `[=JSON-OUTPUT-PATH]`：用于导出 `JSON` 输出文件。

>[!NOTE]
>
> 输出文件夹的默认路径为 `var/output/[TIME]-results.json`.

## HTML报表

在命令行界面上运行HTML时，或通过 [!DNL Site-Wide Analysis Tool]. HTML报表还包含：

- 已识别问题的列表。
- 分析摘要。

![HTML报表 — 摘要](../../assets/upgrade-guide/uct-html-summary.png)

您可以轻松地在以下期间浏览已识别的问题： [!DNL Upgrade Compatibility Tool] 分析。

您可以根据最低问题级别(默认值为 `WARNING`)。

右上角有一个下拉列表，允许您选择其他级别。 已识别的问题列表将相应地被过滤。

![HTML报表 — 下拉菜单使用情况](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 较低问题级别的问题会被剔除，但您会收到通知，这样您就始终能够了解每个模块识别的问题。

HTML报表还包括四个不同的图表：

- **按问题严重性显示的模块**：按模块显示严重性分布。
- **按问题严重性列出的文件**：按文件显示严重性分布。
- **按问题总数排序的模块**：显示10个危害最大的模块，并计入警告、错误和严重错误。
- **具有相对大小和问题的模块**：模块包含的文件越多，其圆圈越大。 模块出现的问题越多，其圆圈显示的红色就越多。

利用这些图表，可识别最容易损坏的模块以及需要更多工作才能执行升级的模块。

![HTML报表 — 图表](../../assets/upgrade-guide/uct-html-diagrams.png)

HTML报表图也会相应地更新，但 `Modules with relative sizes and issues`，使用生成 `min-issue-level` 那是原始设置的。

如果您想查看以下项目的不同结果 `Modules with relative sizes and issues` 图，必须重新运行命令，为 `--min-issue-level` 选项。

![HTML报表 — 气泡图](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

要将此HTML报表导出到其他输出文件夹，请执行以下操作：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

其中参数如下：

- `<dir>`：Adobe Commerce安装目录。
- `[=HTML-OUTPUT-PATH]`：用于导出 `.html` 输出文件。

>[!NOTE]
>
> 输出文件夹的默认路径为 `var/output/[TIME]-results.html`.
