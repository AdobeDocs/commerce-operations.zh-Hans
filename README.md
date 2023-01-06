---
source-git-commit: d17847a7151c5e88f763b334e1ee659ca3ca6bcf
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 5%

---
# Adobe Commerce用户文档

我们欢迎社区成员以及文档团队外的Adobe员工踊跃参与。

## Adobe开源行为准则

本项目已采用 [Adobe 开源行为准则](code-of-conduct.md)或 [.NET Foundation 行为准则](https://dotnetfoundation.org/code-of-conduct)。有关更多信息，请参阅[贡献](contributing.md)文章。

## 关于您对Adobe内容的贡献

请参阅 [Adobe文档参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

您的参与方式取决于您的身份以及您希望参与的更改类型：

### 次要更改

如果您出于善意而提供了一些小更新，请访问文章，然后单击 **编辑** 链接，转到文章的GitHub源。 然后，只需使用GitHub UI进行更新。 请参阅常规 [Adobe文档参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 以了解更多信息。

您为此存储库中的文档和代码示例提交的细微更正或说明均受Adobe使用条款的约束。

### 社区成员所做的重大更改或新文章

如果您是Adobe社区的一员，并且想要创建新文章或提交重大更改，请使用Git存储库中的“问题”选项卡提交问题以开始与文档团队的对话。 一旦您同意了计划，您将需要与员工合作，通过公共和专用存储库中的工作组合来帮助引入新内容。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### 来自Adobe员工的主要更改

如果您是来自Adobe Experience Cloud解决方案产品团队的技术文档撰稿人、项目经理或开发人员，并且您的工作是撰写或创作技术文章，则应使用位于 `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 工具和设置

社区参与者可以使用GitHub UI进行基本编辑，或创建存储库分支以做出重大贡献。

请参阅 [Adobe文档参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 以了解详细信息。

## 如何使用Markdown设置主题格式

此存储库中的所有文章都使用GitHub风格的Markdown。 如果您不熟悉Markdown，请参阅：

* [Markdown基础知识](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [可打印的Markdown速查表](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 标签

在公共存储库中，会为拉取请求分配自动标签，以帮助我们管理拉取请求工作流，并帮助您了解拉取请求的进展情况：

* **已发送给作者的更改**:已通知作者拉取请求处于待处理状态。
* **准备合并**:准备由我们的拉取请求审阅团队进行审阅。

## 模板

的 `_jekyll` 目录包含模板主题和必需资产。
使用液体模板语言的模板位于 `_jekyll/templated` 目录作为HTML文件。
的 `_jekyll/_data` 目录包含包含用于呈现模板的数据的文件。

要渲染所有模板，请执行以下操作：

1. 导航到 `_jekyll` 目录访问Advertising Cloud的帮助。

   cd_jekyll

1. 运行渲染脚本。

```
_scripts/render
```

> **注意：** 必须从 `_jekyll` 目录访问Advertising Cloud的帮助。
> **注意：** 必须安装Ruby才能运行此脚本。

脚本运行渲染并将渲染的模板写入 `help/_includes/templated` 目录访问Advertising Cloud的帮助。

有关 [数据文件](https://jekyllrb.com/docs/datafiles) [液体过滤器](https://jekyllrb.com/docs/liquid/filters/)和其他功能。
