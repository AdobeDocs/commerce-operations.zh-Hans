---
title: 为 [!DNL Adobe Commerce Patching Automation]设置GitHub集成
description: 了解如何安装 [!DNL Adobe Commerce Patching Automation] GitHub应用程序以便为连接到GitHub的Adobe Commerce Cloud项目启用修补程序操作。
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# 为[!DNL Patching Automation]设置GitHub集成

如果您的Adobe Commerce云项目已连接到GitHub存储库，则必须安装[!DNL Patching Automation] GitHub应用程序，然后才能使用该服务来应用或还原修补程序。 应用程序会授予该服务代表您对存储库进行更改所需的访问权限。

## 先决条件

* 有效的Adobe Commerce Cloud订阅
* 已为您的Adobe Commerce Cloud项目配置[GitHub集成](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)，并启用了其[`fetch-branches`选项](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)。 [!DNL Patching Automation]创建并推送临时集成环境分支，因此，在禁用此选项时，修补程序操作无法创建环境。
* 托管在[!DNL github.com]上的存储库。 不支持使用自定义域配置的GitHub集成。
* 对GitHub组织或存储库的所有者或管理员访问权限

## 安装[!DNL Patching Automation] GitHub应用程序

您可以从[!DNL Patching Automation]开始安装，方法是单击UI中的&#x200B;**[!UICONTROL Install GitHub App]**（将您重定向到安装页面），或者直接导航到安装页面。

1. 打开[Patching Automation GitHub应用程序安装页面](https://github.com/apps/adobe-commerce-patching-automation)。
1. 单击&#x200B;**[!UICONTROL Install]**。
1. 选择拥有Adobe Commerce存储库的GitHub组织。
1. 在&#x200B;**[!UICONTROL Repository access]**&#x200B;下，选择&#x200B;**[!UICONTROL Only select repositories]**，然后为您的Adobe Commerce项目选择存储库。
1. 单击&#x200B;**[!UICONTROL Install]**&#x200B;确认。

安装后，该服务将自动检测您的GitHub连接，并将应用程序用于所有修补程序操作。 无需进一步设置。

## 检查并管理连接状态

[!DNL Patching Automation] UI显示GitHub连接的当前状态，并根据该状态提供相应的操作：

* **[!UICONTROL Refresh]** / **[!UICONTROL Refresh status]** — 重新检查连接状态而不进行任何更改。
* **[!UICONTROL Reinstall]** — 在安装不再有效时显示（例如，安装已暂停或连接到您的云项目的存储库已更改）。 启动上述相同的安装流程。
* **[!UICONTROL Unlink GitHub App]** — 删除[!DNL Patching Automation]与GitHub应用程序的已保存连接。 这&#x200B;**不会**&#x200B;从GitHub存储库中卸载应用程序 — 要完全删除访问权限，请参阅下面的“卸载”部分。

## 卸载[!DNL Patching Automation] GitHub应用程序

如果您不再希望服务访问您的存储库：

1. 在GitHub中，打开拥有该安装的帐户的设置：
   * 对于&#x200B;**组织拥有的**&#x200B;存储库： **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**。
   * 对于&#x200B;**个人**&#x200B;存储库： **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**。
1. 找到`adobe-commerce-patching-automation`并单击&#x200B;**[!UICONTROL Configure]**。
1. 单击&#x200B;**[!UICONTROL Uninstall]**&#x200B;并确认。

>[!WARNING]
>
>卸载GitHub应用程序后，如果任何应用或还原操作仍在进行中，则这些操作可能会失败。 卸载应用程序后，用户也无法启动新操作，因为操作按钮已停用。

## 相关主题

* [修补自动化简介](intro.md)
* [如何访问](access.md)
* [工作流概述](workflow.md)
* [最佳实践](best-practices.md)
* [故障排除](troubleshooting.md)
