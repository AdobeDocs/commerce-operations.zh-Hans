---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# 最佳实践：内容创建工作流

本文档介绍了请求更改或添加 *[最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html)* 内容 *Adobe Commerce实施手册*.

## 谁可以创建请求？

Adobe接受来自内部和外部利益相关方的请求，包括但不限于以下群体中的个人：

- Adobe合作伙伴
- AdobeCTAG（客户技术顾问组）、客户支持、客户成功、工程团队

## 如何创建请求？

**内部利益相关方** 可以通过在COMDOX项目中打开Jira问题来提交请求。 **外部利益相关方** 可以通过打开 [GitHub问题](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 。

您可以提交以下类型的请求：

- 新内容的构思
- 已发布内容的更新
- 发布利益相关者或社区提供的新内容

## 整个过程是什么？


**创建Jira票证或问题** — 内部利益相关方在COMDOX项目中创建Jira票证。 外部利益相关方提交GitHub问题。 在Jira或 [GitHub问题](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 以帮助团队了解上下文并排定请求的优先级。

**Adobe项目团队会评估请求并确定其优先级** — 该团队定期监控请求以确定优先级，并评估请求的更改，以将其纳入实施行动手册最佳实践。 例如，团队可能会确定，请求的内容不应当添加到Experience League或Adobe Developer网站上的现有产品文档中，而应该添加到新的“最佳实践”主题。

如果在请求中提供的信息不够，则团队请求请求者提供的附加信息。 如果请求者在14天内未做出响应，则团队将关闭请求。

**创建或更新内容** — 按照 [Adobe Experience League参与者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). 根据请求，工作可包括将新内容转换为Markdown、创建主题或更新现有主题。

**内容审核、批准和发布** — 在创建或更新主题期间，使用 [GitHub拉取请求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). 所有内容都必须经过编辑审查。 技术审查是可选的，具体取决于内容。 如果不需要进行技术审查，则该过程仅继续进行编辑审查。 此过程可能需要多次迭代，直到内容获得批准。

文章获得批准后，拉取请求可合并到生产分支。 合并应由作者完成。 合并主题后，可以使用手动过程立即将其发布到生产环境，或在下次运行发布作业时自动将其发布到生产环境。 发布作业通常每两小时运行一次。

**新内容通知**-Adobe将提供 *新增功能* 部分 [最佳实践概述](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) 主题可让用户了解最近发布或更新的主题。 Adobe还将使用现有渠道（如营销和内部沟通）宣传新的最佳实践内容。

## 积压和看板板

为避免重复，已创建并排定优先顺序的请求将在COMDOX项目积压的Jira中可见， [GitHub问题项目](https://github.com/orgs/AdobeDocs/projects/6/views/1). 鼓励内部利益攸关者与吉拉的投票系统接触，对他们认为必要或相关的请求进行表决。 投票还有助于最佳实践项目团队了解利益相关方期望和有价值的内容类型。 等待确定优先级和审核的请求将显示在积压工作中，直到它们被移动到看板板中的活动通道。

内部用户可以访问看板板，以查看（和/或监视）正在处理的内容和进度。 此展示板上只显示活动请求。
