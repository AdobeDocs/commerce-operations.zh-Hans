---
source-git-commit: 7f23a1b123d2ca2e1d116eb66344a67cfe45e409
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 3%

---
# Adobe Commerce运行技术文档

我们欢迎社区以及文档团队以外的Adobe员工投稿。

## 用于图像优化的预提交挂接

此存储库包括自动预提交挂接，用于在提交之前优化图像。 **所有参与者都应启用这些挂接**，以确保一致的图像优化并降低存储库大小。

### 快速设置

克隆存储库后，运行：

```bash
.githooks/setup-hooks.sh
```

### 钩子做什么

- 自动检测暂存的图像文件(PNG、JPG、JPEG、GIF、SVG)
- 运行`image_optim`以压缩和优化图像
- 自动重新存放优化的图像
- 确保所有提交的映像都得到了正确优化

### 优点

- 减少了存储库大小
- 更快地加载文档的页面
- 所有参与者均具有一致的图像质量
- 无需手动优化

有关详细的设置说明、疑难解答和配置，请参阅[`.githooks/README.md`](.githooks/README.md)。

## Adobe Open Source行为准则

本项目已采用 [Adobe 开源行为准则](code-of-conduct.md)或 [.NET Foundation 行为准则](https://dotnetfoundation.org/code-of-conduct)。有关更多信息，请参阅[贡献](contributing.md)文章。

## 关于您对Adobe内容的投稿

请参阅[Adobe文档参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

您的参与方式取决于您的身份以及您希望参与的更改类型：

### 次要更改

如果您要提供较小的更新，请访问文章，然后单击文章底部显示的反馈区域，单击&#x200B;**详细的反馈选项**，然后单击&#x200B;**建议编辑**&#x200B;以转到GitHub上的Markdown源文件。 使用GitHub UI进行更新。 有关详细信息，请参阅常规的[Adobe Docs参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

您为此存储库中的文档和代码示例提交的小幅度更正或说明受Adobe使用条款的约束。

### 社区成员的重大更改或新文章

如果您是Adobe社区的一员，并且希望创建新文章或提交重大更改，请使用Git存储库中的“问题”选项卡来提交问题，从而开始与文档团队的对话。 在就计划达成共识后，您需要与员工合作，通过公共和专用存储库中的工作组合来帮助引入新内容。

### Adobe员工做出的主要更改

如果您是来自Adobe Experience Cloud解决方案产品团队的技术文档撰稿人、项目经理或开发人员，并且您的工作就是撰写或创作技术文章，那么您应当使用位于`https://git.corp.adobe.com/AdobeDocs`的专用存储库。

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 工具和设置

社区参与者可以使用GitHub UI进行基本编辑或创建存储库分支以进行重大更改。

有关详细信息，请参阅[Adobe Docs参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

## 如何使用Markdown格式化主题

此存储库中的所有文章都使用GitHub风格的标记。 如果您不熟悉Markdown，请参阅：

- [标记基础知识](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [可打印的Markdown速查表](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 模板

对于某些主题，我们使用数据文件和模板来生成已发布的内容。 此方法的用例包括：

- 发布大量以编程方式生成的内容
- 为需要机器可读文件格式（如YAML）以进行集成（如站点范围分析工具）的多个系统中的客户提供单一真实来源

模板化内容的示例包括但不限于：

- [CLI工具引用](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [产品可用性表](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [系统要求表](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### 生成模板化内容

通常，大多数作者只需要将发行版本添加到产品可用性和系统要求表中。 所有其他模板化内容的维护都是自动进行的，或由专门的团队成员管理。 这些说明适用于大多数作者。

>**注释：**
>
>- 生成模板化内容需要在终端中的命令行上工作。
>- 必须安装Ruby才能运行渲染脚本。 有关所需版本，请参阅[_jekyll/.ruby-version](_jekyll/.ruby-version)。

有关模板化内容的文件结构的描述，请参阅以下内容：

- `_jekyll` — 包含模板化主题和所需资源
- `_jekyll/_data` — 包含用于呈现模板的计算机可读文件格式
- `_jekyll/templated` — 包含使用Liquid模板语言的基于HTML的模板文件
- `help/_includes/templated` — 包含模板化内容的生成输出，格式为`.md`，因此可在Experience League主题中发布；渲染脚本自动将生成的输出写入此目录中

要更新模板化内容，请执行以下操作：

1. 在文本编辑器中，打开`/jekyll/_data`目录中的数据文件。 例如：

   - [产品可用性表](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)： `/jekyll/_data/product-availability.yml`
   - [系统要求表](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)： `/jekyll/_data/system-requirements.yml`

1. 使用现有的YAML结构创建条目。

   例如，要将Adobe Commerce版本添加到产品可用性表中，请将以下内容添加到`extensions`文件的`services`和`/jekyll/_data/product-availability.yml`部分中的每个条目（根据需要修改版本号）：

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. 导航到`_jekyll`目录。

   ```bash
   cd _jekyll
   ```

1. 生成模板化内容并将输出写入`help/_includes/templated`目录。

   ```bash
   rake render
   ```

   >**注意：**&#x200B;必须从`_jekyll`目录运行脚本。 如果这是您第一次运行脚本，则必须先使用`bundle install`命令安装Ruby依赖项。

1. 导航回`root`目录。

   ```bash
   cd ..
   ```

1. 验证预期的`help/_includes/templated`文件是否已修改。

   ```bash
   git status
   ```

   您应会看到类似于以下内容的输出：

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. 推送您的更改。

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

有关[Data Files](https://jekyllrb.com/docs/datafiles)、[Liquid Filters](https://jekyllrb.com/docs/liquid/filters/)和其他功能的更多详细信息，请参阅Jekyll文档。
