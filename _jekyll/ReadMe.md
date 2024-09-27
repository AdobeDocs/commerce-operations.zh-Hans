---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# 概述

此项目包括多个Rake任务以自动化工作流的各个方面，例如为新闻摘要生成数据、渲染模板化文件、优化图像和生成地图。 以下是Rakefile中定义的每个Rake任务的说明和使用指南。

## Rake任务

### `render`

使用来自`_jekyll/_data/`的数据呈现`_jekyll/templates`目录中的模板化文件。 结果将在`help/includes/templated`目录中找到。

**用法：**

```sh
rake render
```

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

## 先决条件

- Ruby和Bundler已安装。
- 在Gemfile中指定的必需gems。
- 用于`azure_regions`任务的Python、[PyGMT](https://www.pygmt.org/latest/install.html)和[pdf2svg](https://formulae.brew.sh/formula/pdf2svg)。

## 设置

1. 安装所需的gems：

   ```sh
   bundle install
   ```

2. 确保已为`azure_regions`任务安装Python、PyGMT和pdf2svg。 有关该设置的更多详细信息，请参阅文档(位于[_scripts/azure_regions.py](_scripts/azure_regions.py)的注释中)。
