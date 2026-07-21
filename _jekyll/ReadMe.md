---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---
# 概述

此项目使用Rake任务自动执行部分文档工作流。 大多数任务在ExL Commerce文档存储库之间共享，并来自[`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks) gem。 下面的一些任务特定于此存储库。

**有关常见任务（渲染模板、管理includes、优化/审核图像、生成“新增功能”摘要），请参阅[adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md)。**

> 以下所有`bundle exec rake`命令都必须从`_jekyll/`目录中运行，因为这是Gemfile和Rakefile的生存位置。

## 特定于存储库的Rake任务

### `whatsnew_bp`

在最佳实践中为新闻摘要生成数据。 默认时间范围为自上次更新以来的时间。 您可以使用`since`参数指定其他句点。

**用法：**

```sh
bundle exec rake whatsnew_bp
```

**具有`since`参数：**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `get_released_versions`

从`magento/magento2`存储库获取最近10个已发布的版本。 需要安装和验证[GitHub CLI](https://cli.github.com/)。

**用法：**

```sh
bundle exec rake get_released_versions
```

**输出：**&#x200B;生成具有发行标记名称和日期的`tmp/core-release.txt`。

### `first_merge_date`

获取首次合并到指定分支中的日期。 需要安装和验证[GitHub CLI](https://cli.github.com/)。

**用法：**

```sh
bundle exec rake first_merge_date base=develop
```

**参数：**

- `base` （必需）：要检查合并的目标分支名称。

## 列出可用任务

要查看所有可用的Rake任务及其说明，请使用：

```sh
bundle exec rake --tasks
```

有关特定任务的更多详细信息，请使用：

```sh
bundle exec rake -T [task_name]
```

## 包含关系文件格式

`include-relationships.yml`文件跟踪主内容文件及其包含的文件之间的关系。 此文件由`includes:maintain_relationships`任务自动维护（有关任务使用情况，请参阅[adobe-comdox-exl-rake-tasks自述文件](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md)），该任务通过读取现有的包含文件并查找引用这些文件的主文件来发现关系。

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
- 在Gemfile中指定的必需gems（`adobe-comdox-exl-rake-tasks`提供了常见任务；`whatsnew`任务还需要`whatsup_github`）。
- 用于`get_released_versions`和`first_merge_date`任务的[GitHub CLI](https://cli.github.com/)。

## 设置

安装所需的gems：

```sh
bundle install
```
