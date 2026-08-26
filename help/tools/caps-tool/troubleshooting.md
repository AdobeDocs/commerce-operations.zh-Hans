---
title: '[!DNL Adobe Commerce Patching Automation]疑难解答指南'
description: 对 [!DNL Adobe Commerce Patching Automation]中的常见问题和错误消息进行故障诊断
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]疑难解答指南

使用[!DNL Patching Automation]进行修补程序操作时，可能会遇到错误消息和问题，这些消息和问题可能会阻止修补程序应用程序成功或进行反向。 本指南为最常见的问题提供了解决方案。

## 快速疑难解答步骤

### 如果修补操作失败

* 检查操作状态以了解哪个阶段失败
* 查看特定失败原因的错误消息
* 检查错误日志以了解技术详细信息
* 遵循本指南中提供的解决方案

>[!TIP]
>
>在Cloud Console中，可从项目的活动信息源中获取部署日志 — 即使在删除临时集成环境之后也是如此。

### 修补程序操作持续时间

对于大多数环境，以下时间线描述了修补操作需要多长时间，但具体时间长短取决于环境大小和复杂性：

* **预处理：** 2-5分钟
* **正在修补：** 5-15分钟
* **后处理：** 10-40分钟
* **总计：** 15-60分钟

>[!NOTE]
>
>后处理时间是根据您环境的部署历史记录估计的，因此对于部署速度异常快或速度异常慢的环境，后处理时间可能会超出上述范围。

### 取消正在进行的修补程序

>[!WARNING]
>
>修补程序操作开始后，应允许它完成。 该系统包括即使操作失败也运行的清理过程。 中断进程可能会使您的环境处于不一致的状态。

## 常见成功消息

* **“作业已成功完成”** — 修补程序已成功应用/还原，没有任何问题。

* **“已应用修补程序”** — 您正在尝试应用已应用的修补程序。 系统检测到您的环境中已存在该修补程序。 无需执行任何操作。

* **“修补程序已还原”** — 您正在尝试还原已还原的修补程序。 系统检测到当前未应用修补程序。 无需执行任何操作。

## 常见错误消息和解决方案

>[!NOTE]
>
>并非所有可能的错误都列在下面。 初步检查期间未列出的失败显示为通用的“初步检查期间出错”；验证期间未列出的失败显示为通用的“后处理期间出错” — 请以两种方式联系支持人员，并提供准确的错误文本。 在修补期间，意外故障会直接显示原始基础错误消息，而不是通用回退消息。

### 环境就绪错误

#### “上次部署未成功。 在应用或还原修补程序之前，请确保环境稳定。”

**发生时：**&#x200B;在初步检查开始时，在任何修补程序特定的验证之前

**原因：**&#x200B;目标环境的最新部署未成功完成

**解决方案：**&#x200B;重新部署目标环境并确认部署成功完成（在Cloud Console中检查其部署日志），然后重试修补程序操作。

### 修补应用程序错误

#### “无法应用修补程序，因为[!DNL Patching Automation]检测到您的代码库或修补程序文件存在这些问题”

**发生时间：**&#x200B;初步检查期间

**原因：**&#x200B;修补程序与当前代码库冲突，或者修补程序本身有问题

**解决方案：**

* 查看提供的详细错误日志，确定是代码库问题还是修补程序问题
* 检查代码中是否存在冲突的自定义项
* 验证该修补程序是否与您的Adobe Commerce版本兼容
* 考虑手动解决冲突或联系支持人员

#### “您正在尝试还原未通过[!DNL Patching Automation]应用的修补程序。 可能是手动应用了修补程序。”

**发生时间：**&#x200B;还原操作期间

**原因：**&#x200B;您正在尝试还原未通过[!DNL Patching Automation]应用的修补程序

**解决方案：**&#x200B;使用最初用于应用修补程序的方法，或者与支持人员联系以获得手动帮助

### 环境和验证错误

#### “环境与父环境不同步”

**发生时：**&#x200B;在验证期间，在合并前同步检查中 — 集成环境合并到目标环境之前

**原因：**&#x200B;您的集成环境与父环境不同，通常是因为测试修补程序时目标环境已更改

**解决方案：**

* 一旦目标环境稳定，请重试修补操作
* 避免在修补程序操作正在进行时对目标环境进行更改
* 如果同步问题仍然存在，请联系支持人员

#### “合并后验证失败：环境在合并后不同步。”

**发生时：**&#x200B;在验证期间，集成环境已合并到目标环境中

**原因：**&#x200B;两个环境的代码在合并后不匹配，通常是暂时的Platform.sh API传播延迟，而不是真正的冲突

**解决方案：**

* 请等待几分钟，然后再次检查环境状态。 此问题通常自行解决
* 如果经过几分钟后环境仍然不匹配，请联系Adobe支持部门。

#### “启用cron并禁用维护模式时，无法在生产环境中创建修补程序作业。 请在应用修补程序之前启用维护模式并禁用cron作业。”

**发生时间：**&#x200B;在生产环境的初步检查期间

**原因：**&#x200B;生产环境不符合所需的安全条件

**解决方案：**

* 为生产存储启用维护模式
* 在生产环境中禁用cron作业
* 重试之前验证是否同时满足两个条件
* 或者，选中UI中的覆盖复选框以跳过这些检查并继续。 只有在您了解没有这些保护措施的情况下修补生产环境存在的风险时，才使用覆盖选项

>[!IMPORTANT]
>
> [!DNL Patching Automation]不会自动启用维护模式或禁用cron作业 — 这些作业必须由您在外部完成

#### “修补程序操作已完成，但环境运行状况检查失败。 这表示部署可能存在问题。 请查看环境状态并考虑恢复更改。”

**发生时：**&#x200B;修补程序应用或还原后，验证期间

**原因：**&#x200B;已成功应用或还原修补程序，但后续的运行状况检查失败

**解决方案：**

* 测试店面和关键结账以及管理员工作流，确认客户是否实际受到影响
* 在Cloud Console中，查看环境状态并检查项目&#x200B;**活动**&#x200B;信息源中的应用程序和部署日志。 查找与修补程序操作或部署相关的错误。
* 触发手动重新部署，以确定运行状况检查失败是由临时部署还是基础架构问题引起的。
* 如果问题仍然存在，请还原修补程序。 如果修补程序由[!DNL Patching Automation]管理，并且操作可用，请选择[!UICONTROL Revert]。 如果修补程序是`m2-hotfixes`目录中的自定义修补程序，请从项目存储库中删除该修补程序文件。 提交并推送更改，然后重新部署环境。
* 如果问题仍然存在，请与Adobe支持部门联系。在您的支持请求中包含以下信息：支持项目ID、环境ID，以及此消息：上次操作未完全完成，因此支持部门可能需要确认环境的状态。

### 身份验证和访问错误

#### “访问被拒绝”

**发生时：**&#x200B;当您的帐户在环境创建或访问期间缺少所需的权限时

**原因：**&#x200B;您的用户帐户缺少必要的权限

**解决方案：**

* 检查您的用户角色和权限
* 联系您的系统管理员
* 验证您是否具有环境管理权限
* 确保您具有部署权限

### GitHub集成错误

#### 没有可用于提供程序“github”的Git凭据。 为此存储库安装修补自动化GitHub应用程序”

**发生此情况时：**&#x200B;在连接到GitHub的项目的修补程序操作期间

**原因：**&#x200B;您的存储库上未安装[!DNL Patching Automation] GitHub应用程序

**解决方案：**&#x200B;按照[中为 [!DNL Patching Automation]](github-integration.md)设置GitHub集成中的步骤操作

#### “GitHub API请求失败”

**发生此情况时：**&#x200B;对GitHub连接项目执行修补程序操作期间

**原因：**&#x200B;临时问题导致服务无法连接到GitHub

**解决方案：**&#x200B;请等待几分钟，然后重试该操作。 如果错误仍然存在，请联系[Adobe Commerce云支持](https://experienceleague.adobe.com/home?lang=zh-Hans#support)

#### “未在超时内创建环境”（与GitHub连接的项目）

**发生时间：**&#x200B;集成环境创建期间

**原因：**&#x200B;项目的GitHub集成禁用了`fetch-branches`选项。 因此，服务推送的临时分支不会同步，并且永远不会创建集成环境。

**解决方案：**&#x200B;启用集成的[`fetch-branches`选项](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)，然后重试该操作。 请参阅[为 [!DNL Patching Automation]](github-integration.md)设置GitHub集成。

### 环境激活错误

#### “无法激活集成环境。”

**发生时：**&#x200B;当[!DNL Patching Automation]无法激活安全测试修补程序所需的临时集成环境时。

**原因：**&#x200B;取决于错误旁边显示的其他详细信息：

**如果详细信息提及编辑器或Adobe Commerce包：**

* 登录到[https://account.magento.com/](https://account.magento.com/)（或者让您的帐户所有者执行此操作），并确认您的帐户有权访问Commerce Enterprise代码库。
* 验证项目的编辑器公钥/私钥对是否正确 — 请参阅[身份验证密钥](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/authentication-keys)。
* 登录到[https://account.magento.com/](https://account.magento.com/)（或要求您的帐户所有者执行此操作），并确认您的帐户有权访问Commerce Enterprise代码库。
* 验证项目的编辑器公共身份验证密钥和专用身份验证密钥是否正确。 请参阅[身份验证密钥](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/authentication-keys)。
* 确认错误消息中名为的包适用于您的Commerce版本。 查看[Adobe Commerce包](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/packages/adobe-commerce)。

**如果详细信息提及环境插槽或资源：**

* 在Cloud Console中，打开项目概述并查看环境及其状态。 停用或删除任何未使用的集成环境：选择环境。 转到&#x200B;**[!UICONTROL Settings]>[!UICONTROL General]**。 将环境状态设置为不活动。

  或者，使用CLI： `magento-cloud environment:list` / `magento-cloud environment:deactivate <environment-name>`
* 验证项目是否有足够的资源，例如磁盘空间。
* 确保在操作时父环境稳定（无活动部署）。
* 如果您需要提高环境限制，请联系Adobe支持部门。

**对于任何其他原因：**&#x200B;请查看修补自动化UI中的详细错误日志，或联系支持人员并提供确切的错误文本。

## 获取帮助

**何时联系支持人员：**

在以下情况下联系Adobe Commerce云支持：

* 错误消息不明确或缺少足够的详细信息
* 修补程序操作始终失败
* 您需要手动冲突解决方面的帮助
* 运行状况检查失败，但原因不明
* 您需要有关环境同步问题的帮助

**要提供的信息：**

在联系支持人员时，提供：

* **项目ID** — 您的Adobe Commerce Cloud项目标识符
* **环境ID** — 发生问题的特定环境
* **操作ID** - [!DNL Patching Automation]操作标识符
* **错误详细信息** — 完整的错误消息和日志
* **重现问题的步骤** — 发生错误时您正在做什么
* **以前的尝试** — 您已经尝试解决此问题的内容

### 其他资源

有关更详细的技术信息：

* 查看随失败操作提供的完整错误日志
* 有关特定于修补程序的指南，请查看Adobe Commerce文档
* 有关特定于环境的问题，请联系Adobe Commerce云支持

### 相关主题

* [Adobe Commerce Cloud文档](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/overview)
* [Adobe Commerce安装指南](/help/installation/overview.md)
* [修补自动化简介](intro.md)
* [如何访问](access.md)
* [工作流概述](workflow.md)
* [GitHub集成](github-integration.md)
* [最佳实践](best-practices.md)
