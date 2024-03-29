---
title: 项目实施方法
description: 熟悉Adobe Commerce软件投放的工作方式。
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
feature: Build, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 项目执行方法

现在，您已更好地了解所涉及的工具，我们现在将细分我们的交付和测试流程。

## 持续集成(CI)

连续集成作业会自动执行以下操作：

- 生成源代码以检查编译错误。
- 在创建/更新拉取请求时执行测试。 目前，执行PHP单元测试。

作业将其执行状态发布到拉取请求。 开发人员可以查看作业执行的详细信息，以便修复或改进现有代码。

## 连续投放(CD)

在所有测试成功通过后，连续交付(CD)会立即将源代码部署到服务器。 开发人员可以快速检查其功能，然后将任务分配给QA团队进行审核。

当构建在构建系统上执行时，它不仅可以最大程度地减少部署停机时间，还可以减少服务器上的负载。 因此，发生在服务器上的QA活动受到的影响较小。

![连续投放信息图](../../assets/playbooks/cicd.svg)

上图中的CI/CD过程可简述如下：

- Bitbucket托管Git存储库。
- Docker映像是从生产技术栈栈配置中复制的。
- Docker容器用于所有开发和测试环境。 如果需要，其他环境可以利用这些配置。
- 开发人员会为每个新任务/票证执行相关代码分支的签出。
- 对于所有提交分支，自动：
   - 执行标准代码扫描。
   - 执行代码编译测试。
   - 执行静态代码扫描（例如，SonarQube）。
- 通过的所有扫描提交都将与目标分支合并。
- 新发布的标记将推送到AWS S3，以用于部署就绪包。
- 新部署由部署工程团队触发。
   - 部署作业将新包部署到目标环境。
   - 数据库结构更新需要暂停，才能接受客户的新请求。
- 部署过程以电子邮件/Slack/团队通知结束，该通知由服务器自动发送给部署工程团队。
