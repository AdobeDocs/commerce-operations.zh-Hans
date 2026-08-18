---
title: 为 [!DNL CAPS]设置GitHub集成
description: 了解如何安装 [!DNL Cloud Automation Patching Service (CAPS)] GitHub应用程序以便为连接到GitHub的Adobe Commerce Cloud项目启用修补程序操作。
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# 为[!DNL CAPS]设置GitHub集成

如果您的Adobe Commerce Cloud项目已连接到GitHub存储库，则必须安装[!DNL CAPS] GitHub应用程序，然后才能使用[!DNL Cloud Automation Patching Service] ([!DNL CAPS])应用或还原修补程序。 应用程序授予[!DNL CAPS]代表您对存储库进行更改所需的访问权限。

## 先决条件

* 有效的Adobe Commerce Cloud订阅
* 已为您的Adobe Commerce Cloud项目配置[GitHub集成](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)，并启用了其[`fetch-branches`选项](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)。 [!DNL CAPS]创建并推送临时集成环境分支，因此，在禁用此选项时，修补程序操作无法创建环境。
* 托管在[!DNL github.com]上的存储库。 不支持使用自定义域配置的GitHub集成。
* 对GitHub组织或存储库的所有者或管理员访问权限

## 安装[!DNL CAPS] GitHub应用程序

1. 打开[CAPS GitHub应用程序安装页面](https://github.com/apps/adobe-commerce-patching-automation)。
1. 单击&#x200B;**[!UICONTROL Install]**。
1. 选择拥有Adobe Commerce存储库的GitHub组织。
1. 在&#x200B;**[!UICONTROL Repository access]**&#x200B;下，选择&#x200B;**[!UICONTROL Only select repositories]**，然后为您的Adobe Commerce项目选择存储库。
1. 单击&#x200B;**[!UICONTROL Install]**&#x200B;确认。

安装后，[!DNL CAPS]会自动检测您的GitHub连接，并将应用程序用于所有修补程序操作。 无需进一步设置。

## 卸载[!DNL CAPS] GitHub应用程序

如果您不再希望[!DNL CAPS]访问您的存储库：

1. 在GitHub中，打开拥有该安装的帐户的设置：
   * 对于&#x200B;**组织拥有的**&#x200B;存储库： **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**。
   * 对于&#x200B;**个人**&#x200B;存储库： **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**。
1. 找到`adobe-commerce-patching-automation`并单击&#x200B;**[!UICONTROL Configure]**。
1. 单击&#x200B;**[!UICONTROL Uninstall]**&#x200B;并确认。

>[!WARNING]
>
>如果卸载GitHub应用程序时仍存在任何大写应用或还原操作，则这些操作可能会失败。 卸载应用程序后，用户也无法启动新操作，因为操作按钮已停用。

## 相关主题

* [CAPS介绍](intro.md)
* [如何访问](access.md)
* [工作流概述](workflow.md)
* [最佳实践](best-practices.md)
* [故障排除](troubleshooting.md)
