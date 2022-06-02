---
title: '"[!DNL Upgrade Compatibility Tool] 报告”'
description: 按照以下步骤运行 [!DNL Upgrade Compatibility Tool] 在您的Adobe Commerce项目上。
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 报告

{{commerce-only}}

由于分析结果， [!DNL Upgrade Compatibility Tool] 导出一个报表，其中包含每个文件的问题列表，以指定其严重性、错误代码和错误描述。

请参阅以下示例：

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

检查 [错误消息引用](../upgrade-compatibility-tool/error-messages.md) 主题以了解更多信息。

该报表还包含一个详细的摘要，其中显示：

- *当前版本*:当前安装的版本。
- *Target版本*:要升级到的版本。
- *执行时间*:分析构建报表所花费的时间(mm:ss)。
- *需要更新的模块*:包含兼容性问题和需要更新的模块的百分比。
- *需要更新的文件*:包含兼容性问题和需要更新的文件的百分比。
- *严重错误总数*:发现的严重错误数。
- *错误总数*:找到的错误数。
- *警告总数*:找到的警告数。

请参阅以下示例：

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>默认情况下， [!DNL Upgrade Compatibility Tool] 将报表导出为两种不同的格式： `json` 和 `html`.

## JSON文件

JSON文件包含的信息与输出中显示的信息完全相同：

- 已识别问题的列表。
- 分析摘要。

对于每个遇到的问题，报表会提供详细信息，如问题的严重性和描述。

要将此报表导出到其他输出文件夹，请运行：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

其中参数如下所示：

- `<dir>`:Adobe Commerce安装目录。
- `[=JSON-OUTPUT-PATH]`:导出的路径目录 `.json` 输出文件。

>[!NOTE]
>
>输出文件夹的默认路径为 `var/output/[TIME]-results.json`.

## HTML报表

HTML文件还包含分析摘要和已识别问题的列表。 在命令行界面上运行该工具时，或通过 [!DNL Site-Wide Analysis Tool].

![HTML报表 — 摘要](../../assets/upgrade-guide/uct-html-summary.png)

在 [!DNL Upgrade Compatibility Tool] 分析：

![HTML报表 — 详细信息](../../assets/upgrade-guide/uct-html-details.png)

HTML报表还包含四个不同的图表：

- **按问题严重性划分的模块**:显示按模块划分的严重性分布。
- **按问题严重性列出的文件**:按文件显示严重性分布。
- **按问题总数排序的模块**:显示10个受损最多的模块，其中考虑了警告、错误和严重错误。
- **具有相对大小和问题的模块**:模块包含的文件越多，其圆圈就越大。 模块遇到的问题越多，其圆就越红。

通过这些图表，您可以（一目了然地）识别最易损坏的部件以及执行升级需要更多工作的部件。

![HTML报表 — 图](../../assets/upgrade-guide/uct-html-diagrams.png)

您可以根据最小问题级别过滤报表中显示的问题。 默认值为 `WARNING`.

右上角有一个下拉菜单，允许您根据自己的必需品选择其他选项。 将相应地过滤已识别问题的列表。

![HTML报表 — 下拉列表使用情况](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

请注意，问题级别较低的问题已清除，但您收到通知，以便始终了解每个模块已识别的问题。

此外，图表也会相应地更新，但 `Modules with relative sizes and issues`，通过 `min-issue-level` 最初设置。

如果要查看不同的结果，则需要重新运行为 `--min-issue-level` 选项。

![HTML报表 — 泡泡图图](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

要将此报表导出到其他输出文件夹，请运行：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

其中参数如下所示：

- `<dir>`:{{site.data.var.ee}}安装目录。
- `[=HTML-OUTPUT-PATH]`:导出的路径目录 `.html` 输出文件。

>[!NOTE]
>
> 输出文件夹的默认路径为 `var/output/[TIME]-results.html`.
