---
title: 如何访问 [!DNL Cloud Automation Patching Service (CAPS)]
description: 了解如何访问和使用 [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# 如何访问[!DNL Cloud Automation Patching Service (CAPS)]

## 先决条件

[!DNL CAPS]使用Adobe Commerce Cloud中基于角色的访问控制。 您在Cloud Console中的访问级别决定了您可以对[!DNL CAPS]执行的操作。

### 可以使用[!DNL CAPS]的人员

* **项目管理员** — 可以在所有环境中应用或还原修补程序
* **参与者** — 可以在其分配的环境中应用或还原修补程序
* **查看器** — 只能查看项目和环境，不允许执行任何操作

### 如何请求对项目的访问权限

如果您在[!DNL CAPS]用户界面中未看到任何项目，则需要向相应人员请求访问权限：

* 联系项目的帐户所有者或项目管理员
* 他们将通过Cloud Console授予您适当的角色
* 授予访问权限后，您可以登录到Cloud Console以使用[!DNL CAPS]

>[!NOTE]
>
>[!DNL CAPS]遵循与Adobe Commerce Cloud相同的权限模型，因此您在Cloud Console中的访问级别决定了您可以对[!DNL CAPS]执行的操作。

## 正在访问[!DNL CAPS]

CAPS工具可从站点范围分析工具仪表板中获取，网址为[https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)。 在“自动修补”选项卡下，您可以选择您的项目和环境。

1. 导航到[https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)上的站点范围分析工具。
1. 单击界面中的[!UICONTROL Patching Automation]选项卡。
1. 选择要应用修补程序的项目和环境。
1. 查看可用的修补程序及其兼容性状态。
1. 选择要应用或还原的修补程序。

## 生产环境访问

对于生产环境，可以应用额外的保护措施：

* **维护模式** — 必须启用
* **Cron作业** — 必须禁用
* **确认对话框** — 必须先完成，然后才能继续

>[!IMPORTANT]
>
>生产环境修补需要适当的准备和防护措施，以防止意外中断。

## 相关主题

* [CAPS介绍](intro.md)
* [工作流](workflow.md)
* [最佳实践](best-practices.md)
* [故障排除](troubleshooting.md)
