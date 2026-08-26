---
title: 如何访问 [!DNL Adobe Commerce Patching Automation]
description: 了解如何访问和使用 [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# 如何访问[!DNL Adobe Commerce Patching Automation]

## 先决条件

[!DNL Patching Automation]使用Adobe Commerce Cloud中基于角色的访问控制。 您在Cloud Console中的访问级别决定了您可以使用该服务执行的操作。

### 可以使用[!DNL Patching Automation]的人员

* **项目管理员** — 可以在所有环境中应用或还原修补程序
* **参与者** — 可以在其分配的环境中应用或还原修补程序
* **查看器** — 只能查看项目和环境，不允许执行任何操作

### 如何请求对项目的访问权限

如果您在[!DNL Patching Automation]用户界面中未看到任何项目，请向相应的人员请求访问权限：

* 联系项目的帐户所有者或项目管理员
* 他们将通过Cloud Console授予您适当的角色
* 授予访问权限后，您可以登录到Cloud Console以使用服务

>[!NOTE]
>
>[!DNL Patching Automation]遵循与Adobe Commerce Cloud相同的权限模型，因此您在Cloud Console中的访问级别决定了您可以使用该服务执行的操作。

## 正在访问[!DNL Patching Automation]

[!DNL Patching Automation]在[!DNL Site-Wide Analysis Tool]仪表板中作为选项卡提供。 您可以在管理员侧边栏中转到&#x200B;**报告** > **系统分析** > **网站范围分析工具**，从管理员面板访问该工具。 请参阅[如何访问全站点分析工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access)，了解先决条件和权限设置。

进入仪表板后：

1. 单击界面中的[!UICONTROL Patching Automation]选项卡。
1. 选择要应用修补程序的项目和环境。
1. 查看可用的修补程序及其兼容性状态。
1. 选择要应用或还原的修补程序。

## 生产环境访问

对于生产环境，默认情况下应用其他保护措施：

* **维护模式** — 必须启用
* **Cron作业** — 必须禁用
* **确认对话框** — 必须先完成，然后才能继续

>[!IMPORTANT]
>
>生产环境修补需要适当的准备和防护措施，以防止意外中断。

>[!NOTE]
>
>您可以通过选中UI (*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*)中的覆盖复选框来跳过维护模式和cron-job检查。 只有在您了解没有这些安全保护机制的情况下修补生产环境的风险时，才使用此选项。

## 相关主题

* [修补自动化简介](intro.md)
* [工作流概述](workflow.md)
* [GitHub集成](github-integration.md)
* [最佳实践](best-practices.md)
* [故障排除](troubleshooting.md)
