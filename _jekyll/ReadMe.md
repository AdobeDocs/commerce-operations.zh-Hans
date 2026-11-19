---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
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

### `whatsnew_consolidated`

将已发布的Commerce文档项目中的新增功能表整合到`help/_includes/automated/whatsnew/consolidated.md`中。

```sh
bundle exec rake whatsnew_consolidated
```

在[`_config.yml`](_config.yml)中配置`whatsnew_consolidated.projects`下的项目。 每个条目都需要存储库名称、项目标题和绝对HTTP网站URL：

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/zh-hans/docs/commerce
```

移动条目以更改节顺序。 您可以从两个平台自由地交错项目。 以`.en`结尾的存储库名称使用ExL源路径`help/_includes/templated/whats-new.md`。 所有其他存储库都使用DevSite源路径`src/pages/_includes/templated/whats-new.md`。

该任务从`AdobeDocs` GitHub组织中提取公共`main`文件。 它将每个项目标题显示为纯文本标题，并在每个表中引入一个句子，该句子将项目标题链接到`website`中配置的文档主页，作为“新增功能”更新的源。 它在整个过程中使用`Description | Type | Date/source`表头。 仅对于DevSite项目，转义的`\<br/\>`标记将变为`<br/>`。 否则，正文行、重复项、链接和源行顺序将保持不变。 每个源定义自己的时间段。

将忽略具有已识别的no-updates消息的项目。 如果每个项目都没有条目，则“包含”包含一条总体上的不更新消息。 配置、获取、解析或写入失败会导致任务失败，而不会替换现有的include。

该任务不会计划生成或更新使用页面。

重点测试套件包括加载`_jekyll` Rakefile并通过Bundler运行的Rake入口点测试。 首先安装捆绑包和`_jekyll`捆绑包：

```sh
cd _jekyll && bundle install
```

然后，从存储库根目录运行测试：

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

通过筛选现有的本地`help/_includes/automated/whatsnew/consolidated.md`包含来创建`help/_includes/automated/whatsnew/consolidated-feedback.md`。

```sh
bundle exec rake whatsnew_feedback
```

任务匹配`Feedback`作为完整的逗号分隔类型值，忽略大小写和周围的空格。 已包括`Feedback, technical`等组合类型。 描述、源链接或部分类型名称中的提及不符合条件。

匹配行、重复项、纯文本项目标题、源句子（如果存在）以及项目和行顺序保持不变。 省略没有匹配条目的项目。 如果没有任何匹配，输出将包含一个总体无反馈消息。

输入必须已存在。 当您要刷新`bundle exec rake whatsnew_consolidated`时，请单独运行它。 反馈任务不会获取远程内容、读取项目配置或重新生成其输入。

缺少输入或输入格式错误会导致任务失败，而不会替换现有的已过滤包含。 输入文件永远不会被修改，过滤的输出会自动发布。

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
