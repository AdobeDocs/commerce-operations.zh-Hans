---
title: Git分支最佳实践
description: 了解源代码管理的不同分支策略。
feature: Best Practices
role: Developer
source-git-commit: 9b1c3f7ca56cb6baf262bbd4abc732a30a7eb0ed
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Git分支最佳实践

源代码在开发过程中会经历多个稳定性阶段：

- 主动开发
- 初始代码集成
- 用于质量保证(QA)的代码集成
- 用于最终用户验收测试(UAT)的代码集成
- 生产版本的最终代码集成

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 分支管理

每个开发阶段都应在Git中具有相应的分支，以跟踪代码更改并简化部署过程：

- **任务分支** — 开发人员在实施特定任务（如功能和错误修复）时提交各自的代码更改。
- **开发分支** — 多个开发人员将各自任务分支中的更改合并到单个开发分支以进行自动化集成测试。 此分支将部署到开发环境。
- **QA分支** — 开发人员在开发完成后合并更改，并且代码已通过所有自动集成测试和代码审查。 此分支将部署到QA环境，以进行手动QA测试。
- **稳定/UAT分支** — 在代码通过手动QA测试后进行合并的位置。 此分支部署到UAT环境以进行用户验收测试。
- **生产/发布分支** — 在代码通过UAT后进行合并的位置。 此分支将部署到生产环境，以供发布使用。

>[!TIP]
>
>云基础架构项目上的Adobe Commerce包含对应于不同环境的特定分支。 请参阅 [Pro项目工作流](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) 和 [入门项目工作流](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) 在 _云指南_.

## 分支策略

您可以使用多种分支策略。 选择最适合您的开发团队和复杂项目的策略。

有关更多信息，请参阅以下外部资源：

- [分支工作流](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [分布式工作流](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [用于管理源代码分支的模式](https://martinfowler.com/articles/branching-patterns.html)
- [成功的Git分支模型](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub流](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab流程](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
