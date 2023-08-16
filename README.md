---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 5%

---
# Adobe Commerce技术文档

我们欢迎社区成员以及文档团队以外的Adobe员工踊跃参与。

## Adobe开源项目行为准则

本项目已采用 [Adobe 开源行为准则](code-of-conduct.md)或 [.NET Foundation 行为准则](https://dotnetfoundation.org/code-of-conduct)。有关更多信息，请参阅[贡献](contributing.md)文章。

## 关于您对Adobe内容的投稿

请参阅 [Adobe文档参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

您的参与方式取决于您的身份以及您希望参与的更改类型：

### 次要更改

如果您出于善意想要对文章进行次要更新，请访问文章，然后单击 **编辑** 文章中的链接，可转至文章的GitHub源。 然后，只需使用GitHub UI即可进行更新。 查看常规 [Adobe文档参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 以了解更多信息。

您为此存储库中的文档和代码示例提交的小幅度更正或说明受Adobe使用条款的约束。

### 社区成员的重大更改或新文章

如果您是Adobe社区的成员，并且希望创建新文章或提交重大更改，请使用Git存储库中的“问题”选项卡来提交问题，以便与文档团队开始对话。 在就计划达成共识后，您需要与员工合作，通过公共和专用存储库中的工作组合来帮助引入新内容。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### 来自Adobe员工的重大更改

如果您是来自Adobe Experience Cloud解决方案产品团队的技术文档撰稿人、项目经理或开发人员，并且您的工作就是撰写或创作技术文章，那么您应当使用位于的专用存储库 `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 工具和设置

社区参与者可以使用GitHub UI进行基本编辑或创建存储库分支以进行重大更改。

请参阅 [Adobe文档参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 以了解详细信息。

## 如何使用Markdown格式化主题

此存储库中的所有文章都使用GitHub风格的标记。 如果您不熟悉Markdown，请参阅：

* [Markdown基础](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [可打印的Markdown速查表](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 模板

此 `_jekyll` 目录包含模板化主题和所需资源。
使用Liquid templating语言的模板位于 `_jekyll/templated` 目录作为HTML文件。
此 `_jekyll/_data` 目录包含带有用于呈现模板的数据的文件。

要呈现所有模板，请执行以下操作：

1. 导航至 `_jekyll` 目录。

   cd _jekyll

1. 运行渲染脚本。

```
_scripts/render
```

> **注意：** 您必须从以下位置运行脚本： `_jekyll` 目录。
> **注意：** 必须安装Ruby才能运行此脚本。

脚本运行渲染并将渲染的模板写入 `help/_includes/templated` 目录。

有关更多详细信息，请参阅Jekyll文档 [数据文件](https://jekyllrb.com/docs/datafiles)， [液体过滤器](https://jekyllrb.com/docs/liquid/filters/)和其他功能。
