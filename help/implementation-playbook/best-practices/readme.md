---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# 最佳实践：内容创建工作流

本文档介绍了请求对进行更改或添加的用户工作流。 *[最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* 中的内容 *Adobe Commerce实施行动手册*.

## 谁可以创建请求？

Adobe接受来自内部和外部利益相关者的请求，包括但不限于以下组中的个人：

- Adobe合作伙伴
- AdobeCTAG（客户技术顾问组）、客户支持、客户成功、工程团队

## 如何创建请求？

**内部利益相关者** 可以通过在COMDOX项目中打开Jira问题来提交请求。 **外部利益相关者** 可以通过打开 [GitHub问题](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 在此存储库中。

您可以提交以下类型的请求：

- 关于新内容的想法
- 已发布内容的更新
- 发布利益相关者或社区提供的新内容

## 整个过程是怎样的？


**创建Jira票证或问题** — 内部利益相关者在COMDOX项目中创建Jira票证。 外部利益相关者提交GitHub问题。 在Jira中包含完整详细信息或 [GitHub问题](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 帮助团队了解上下文并优先考虑请求。

**Adobe项目团队会评估请求并为其设置优先级** — 团队定期监控请求以确定优先级，并评估请求的更改以纳入《实施行动手册》最佳实践。 例如，团队可能确定应将请求的内容添加到Experience League或Adobe Developer网站上的现有产品文档中，而不是创建新的最佳实践主题。

如果请求中未提供足够的信息，团队会向请求者请求其他信息。 如果请求者未在14天内作出响应，团队将关闭请求。

**创建或更新内容** — 内容创建工作按照 [Adobe Experience League参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). 根据请求，工作可能包括将新内容转换为Markdown、创建主题或更新现有主题。

**内容审查、批准和发布** — 内容在主题创建或更新过程中使用进行审阅和编辑 [GitHub拉取请求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). 所有内容都必须经过编辑审核。 技术审查是可选的，具体取决于内容。 如果不需要技术审查，该过程将只继续进行编辑审查。 在内容获得批准之前，此过程可能需要多次迭代。

文章获得批准后，拉取请求可以合并到生产分支。 合并应由作者完成。 在合并主题后，可以使用手动过程立即将其发布到生产环境，也可以在下次运行发布作业时自动发布该主题。 发布作业通常每两小时运行一次。

**新内容通知**-Adobe将提供 *新增功能* 部分 [最佳实践概述](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) 用于通知用户最近发布或更新主题的主题。 Adobe还将利用现有渠道（如营销和内部沟通）推广新的最佳实践内容。

## 积压工作和Kanban板

为避免重复，已创建并排定优先次序的请求将显示在COMDOX项目的Jira积压中，并且 [github问题项目](https://github.com/orgs/AdobeDocs/projects/6/views/1). 鼓励内部利益攸关方与Jira的投票系统接触，以投票支持其认为必要或相关的请求。 投票还有助于最佳实践项目团队了解利益相关者期望的内容类型和价值。 待定优先级和审阅的请求会显示在积压中，直到它们移至Kanban展示板中的活动路线为止。

内部用户可以访问Kanban展示板以查看（和/或监控）正在处理的内容以及进度。 此展示板上只显示活动请求。
