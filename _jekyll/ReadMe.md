---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---
# 概述

此项目包括多个Rake任务以自动化工作流的各个方面，例如为新闻摘要生成数据、渲染模板化文件、优化图像和生成地图。 以下是Rakefile中定义的每个Rake任务的说明和使用指南。

## Rake任务

### `render`

使用来自`_jekyll/templates`的数据呈现`_jekyll/_data/`目录中的模板化文件。 结果将在`help/includes/templated`目录中找到。 此任务在呈现后自动维护包含关系和时间戳。

**用法：**

```sh
rake render
```

**它的功能：**
- 执行渲染脚本以生成模板化文件
- 运行`includes:maintain_all`以更新包含关系和时间戳
- 确保所有包含元数据在渲染后为当前元数据

### `image_optim`

优化已修改但未提交文件中的图像。 对于其他图像，请使用`path`参数指定目录或文件。

**用法：**

```sh
rake image_optim
```

**具有`path`参数：**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

为新闻摘要生成数据。 默认时间范围为自上次更新以来的时间。 您可以使用`since`参数指定其他句点。

**用法：**

```sh
rake whatsnew
```

**具有`since`参数：**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

在最佳实践中为新闻摘要生成数据。 默认时间范围为自上次更新以来的时间。 您可以使用`since`参数指定其他句点。

**用法：**

```sh
rake whatsnew_bp
```

**具有`since`参数：**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

生成Azure区域映射。 输入数据文件应放在`_jekyll/tmp/azure-regions.json`中。 将在`_jekyll/tmp/azure-regions.svg`中找到结果。 请注意，您需要安装Python、[PyGMT](https://www.pygmt.org/latest/install.html)和[pdf2svg](https://formulae.brew.sh/formula/pdf2svg)。

**用法：**

```sh
rake azure_regions
```

### `get_released_versions`

从`magento/magento2`存储库获取最近10个已发布的版本。 需要安装和验证[GitHub CLI](https://cli.github.com/)。

**用法：**

```sh
rake get_released_versions
```

**输出：**&#x200B;生成具有发行标记名称和日期的`tmp/core-release.txt`。

### `first_merge_date`

获取首次合并到指定分支中的日期。 需要安装和验证[GitHub CLI](https://cli.github.com/)。

**用法：**

```sh
rake first_merge_date base=develop
```

**参数：**

- `base` （必需）：要检查合并的目标分支名称。

### `includes:maintain_relationships`

通过使用模式`include-relationships.yml`扫描`help`目录中的所有Markdown文件以查找Include语句，从而发现并更新`{{$include /help/_includes/filename.md}}`文件。 此任务自动维护主内容文件及其包含的文件之间的关系。

**用法：**

```sh
rake includes:maintain_relationships
```

**它的功能：**
- 从`help/_includes`目录读取现有包含文件的列表
- 搜索所有主要Markdown文件，以查找引用每个文件的文件，包括
- 使用`{{$include /help/_includes/filename.md}}`模式标识引用
- 使用发现的关系更新`include-relationships.yml`文件
- 提供所做更改的摘要并识别未引用的内容

### `includes:maintain_timestamps`

通过将最新的包含文件更改时间戳添加到主文件来维护包含时间戳。 此任务读取`include-relationships.yml`文件，检查每个包含文件的git历史记录，并在主文件末尾添加或更新时间戳。

**用法：**

```sh
rake includes:maintain_timestamps
```

**它的功能：**
- 加载包含来自`include-relationships.yml`的关系
- 对于每个主文件，在其包含文件中查找最新的git提交日期
- 在主文件末尾添加或更新带有时间戳的HTML注释
- 使用格式： `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- 提供详细的输出，显示已检查的包含文件及其时间戳

**示例输出：**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

同时按顺序运行`includes:maintain_relationships`和`includes:maintain_timestamps`的方便任务。 这是保持包含关系和时间戳的推荐方法。

**用法：**

```sh
rake includes:maintain_all
```

### `unused_includes`

在`help/_includes`目录中查找未由任何Markdown文件引用的包含文件。 这有助于识别可安全删除的孤立的include文件。

**用法：**

```sh
rake unused_includes
```

## 列出可用任务

要查看所有可用的Rake任务及其说明，请使用：

```sh
rake --tasks
```

有关特定任务的更多详细信息，请使用：

```sh
rake -T [task_name]
```

## 包括管理任务

所有与包含相关的任务都在`includes`命名空间下组织，以便更好地组织：

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## 包含关系文件格式

`include-relationships.yml`文件跟踪主内容文件及其包含的文件之间的关系。 此文件由`maintain_include_relationships` rake任务自动维护，该任务通过读取现有的包含文件并查找引用这些文件的主文件来发现关系。

**文件结构：**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**字段：**
- `metadata.last_updated`：上次更新的时间戳
- `metadata.total_relationships`：包含include的主文件总数
- `metadata.auto_discovered`：表示文件是自动生成的
- `metadata.discovery_date`：首次发现关系的日期
- `relationships`：主文件映射到它们包含的文件

**Include语句格式：**
主内容文件使用以下语法来包含其他文件：

```markdown
{{$include /help/_includes/filename.md}}
```

## 先决条件

- Ruby和Bundler已安装。
- 在Gemfile中指定的必需gems（`adobe-comdox-exl-rake-tasks`提供了核心依赖项）。
- 用于[和](https://cli.github.com/)任务的`get_released_versions`GitHub CLI`first_merge_date`。
- 用于[任务的Python、](https://www.pygmt.org/latest/install.html)PyGMT[和](https://formulae.brew.sh/formula/pdf2svg)pdf2svg`azure_regions`。

## 设置

1. 安装所需的gems：

   ```sh
   bundle install
   ```

2. 确保已为`azure_regions`任务安装Python、PyGMT和pdf2svg。 有关该设置的更多详细信息，请参阅文档(位于[_scripts/azure_regions.py](_scripts/azure_regions.py)的注释中)。
