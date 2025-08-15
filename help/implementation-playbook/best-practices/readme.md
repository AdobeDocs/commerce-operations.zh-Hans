---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# 最佳实践：内容创建工作流

本文档描述了用户请求对&#x200B;*[Adobe Commerce实施行动手册]中的*&#x200B;最佳实践&#x200B;*(https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html*)内容进行更改或添加的工作流。

## 谁可以创建请求？

Adobe接受来自内部和外部利益相关者的请求，包括但不限于以下组中的个人：

- Adobe合作伙伴
- Adobe CTAG（客户技术顾问组）、客户支持、客户成功、工程团队

## 如何创建请求？

**内部利益相关者**&#x200B;可以通过在COMDOX项目中打开Jira问题来提交请求。 **外部利益相关者**&#x200B;可以通过在此存储库中打开[GitHub问题](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose)来提交请求。

您可以提交以下类型的请求：

- 关于新内容的想法
- 已发布内容的更新
- 发布利益相关者或社区提供的新内容

## 整个过程是怎样的？


**创建Jira票证或问题** — 内部利益相关者在COMDOX项目中创建Jira票证。 外部利益相关者提交GitHub问题。 在Jira或[GitHub问题](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose)中包含完整的详细信息，以帮助团队了解上下文并设置请求的优先级。

**Adobe项目团队评估请求并排定其优先级** — 团队定期监控请求以确定优先级，并评估请求的更改以纳入《实施行动手册最佳实践》。 例如，团队可能确定应将请求的内容添加到Experience League或Adobe Developer网站上的现有产品文档，而不是创建新的最佳实践主题。

如果请求中未提供足够的信息，团队会向请求者请求附加信息。 如果请求者未在14天内作出响应，团队将关闭请求。

**创建或更新内容** — 按照[Adobe Experience League参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)中记录的过程完成内容创建工作。 根据请求，工作可能包括将新内容转换为Markdown、创建主题或更新现有主题。

**内容审阅、批准和发布** — 内容在主题创建或更新期间使用[GitHub拉取请求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests)进行审阅和编辑。 所有内容都必须经过编辑审核。 技术审查是可选的，具体取决于内容。 如果不需要进行技术审查，则仅继续进行编辑审查。 在内容获得批准之前，此过程可能需要多次迭代。

文章获得批准后，拉取请求可以合并到生产分支。 合并应由作者完成。 在合并主题后，可以使用手动过程立即将其发布到生产环境，也可以在下次发布作业运行时自动发布。 发布作业通常每两小时运行一次。

**新内容通知**-Adobe将提供有关&#x200B;*最佳实践概述*&#x200B;主题的[新增功能](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en)部分，以随时向用户告知最近发布或更新的主题。 Adobe还将利用现有渠道（如营销和内部沟通）推广新的最佳实践内容。

## 积压工作和Kanban板

为避免重复，已创建和排定优先级的请求将显示在COMDOX项目和[GitHub问题项目](https://github.com/orgs/AdobeDocs/projects/6/views/1)的Jira积压中。 鼓励内部利益攸关方与Jira的投票系统合作，以投票表决其认为必要或相关的请求。 投票还有助于最佳实践项目团队了解利益相关者期望的内容类型和价值。 等待优先化和审查的请求会显示在积压中，直到它们移至Kanban展示板中的活动通道为止。

内部用户可以访问Kanban展示板以查看（和/或监控）正在处理的内容以及进展情况。 此展示板上只显示活动请求。
