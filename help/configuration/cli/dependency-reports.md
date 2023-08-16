---
title: 依赖关系报表
description: 创建显示模块、循环和框架依赖关系总计的报表。
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# 依赖关系报表

{{file-system-owner}}

您可以运行以下类型的报表：

- **模块依赖关系**：显示模块之间的依赖关系总数以及依赖关系是硬依赖还是软依赖。
- **循环依赖关系**：显示依赖关系链的总数以及每个模块的循环依赖关系的数量和列表。
- **框架依赖关系**：按模块显示Commerce框架上的依赖项总数（包括每个库的框架条目总数）。

注释中的依赖项也是依赖项。

## 运行依赖关系报表

命令选项：

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

下表说明了此命令的选项、参数和值。

| 参数 | 值 | 必需？ |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | 模块依赖关系报表。 | 是 |
| `show-modules-circular` | 循环依赖关系报表。 | 是 |
| `show-framework` | 框架依赖关系报表。 | 是 |
| `-d --directory` | 要开始搜索报表数据的基目录的路径。 | 否 |
| `-o --output` | 指定报表的逗号分隔值(csv)输出文件的绝对文件系统路径和文件名。 | 否 |

如果没有将目录或文件名作为参数传递，则使用以下应用程序根目录作为默认目录，并使用以下默认文件名：

| 命令 | 文件名 |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### 模块依赖关系报表示例

以下是示例模块依赖关系报表输出的一部分：

```terminal
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### 循环依赖关系报表示例

以下是示例循环依赖关系报告的输出的一部分：

```terminal
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### 框架依赖关系报表示例

以下是示例框架依赖关系报表输出的一部分：

```terminal
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
