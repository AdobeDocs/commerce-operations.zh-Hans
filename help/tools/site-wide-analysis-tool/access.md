---
title: 如何访问 [!DNL Site-Wide Analysis Tool]
description: 了解如何从Adobe Commerce管理面板访问网站范围的分析工具仪表板。 了解用户权限和角色要求。
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# 如何访问[!DNL Site-Wide Analysis Tool]

您可以从商店的[!DNL Site-Wide Analysis Tool]访问[!UICONTROL Admin Panel]仪表板。

[!DNL Site-Wide Analysis Tool]服务可在[生产模式](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/tools/developer-tools#operation-modes)下供有权访问用户[!UICONTROL Admin]角色资源[的](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/user-accounts/permissions-user-roles)用户使用。

>[!NOTE]
>
>自2024年4月23日起，[!DNL Site-Wide Analysis Tool]已停用，不再供Adobe Commerce本地客户使用。


![站点范围分析仪表板](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]仪表板*

>[!NOTE]
>
>您的帐户应有权使用&#x200B;**[!DNL Support Permissions]**&#x200B;以访问[!DNL Site-Wide Analysis Tool Dashboard]。
>&#x200B;>请参阅用户指南中的[共享 [!DNL Commerce] 帐户](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html?lang=zh-Hans)中的更多详细信息。

## 从应用商店的[!DNL Site-Wide Analysis Tool Dashboard]登录到[!UICONTROL Admin Panel]

### 步骤1：验证权限

验证[!UICONTROL Admin]用户帐户是否有权通过其[!DNL Site-Wide Analysis Tool]分配的用户角色[访问](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/user-accounts/permissions-user-roles)。

>[!IMPORTANT]
>
>[!DNL Site-Wide Analysis Tool]角色资源（权限）是&#x200B;**非**&#x200B;自动分配的。 必须为[!UICONTROL Admin]中的用户角色和单独分配给每个用户帐户的角色激活它。

对于需要[!DNL Site-Wide Analysis Tool]访问权限的自定义角色，请执行以下操作：

1. 选择&#x200B;**[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**&#x200B;角色资源。

   ![站点范围分析仪表板](../../assets/tools/swat-role-access.png)
   已为角色&#x200B;*[!DNL Site-Wide Analysis Tool]选择*&#x200B;权限

1. 单击&#x200B;**[!UICONTROL Save Role]**。

1. 通知任何分配了该角色的用户注销[!DNL Admin]，然后重新登录。

>[!NOTE]
>
>如果您已验证用户帐户具有访问[!DNL Site-Wide Analysis Tool]的权限，并且用户在尝试从[!UICONTROL Admin]访问该工具时收到403错误，则云基础架构上的Adobe Commerce实例可能已启用HTTP访问控制。 如果您启用了HTTP身份验证，则不支持[!DNL Site-Wide Analysis Tool]仪表板。 有关解决此问题的更多信息，请参阅我们的[支持文章](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento)。

### 步骤2：访问[!DNL Site-Wide Analysis Tool]

1. 在&#x200B;*[!UICONTROL Admin]*&#x200B;侧边栏上，转到&#x200B;**[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**。

   ![站点范围分析仪表板](../../assets/tools/ac-admin-panel-marked.jpg)
   在Adobe Commerce *[!DNL Site-Wide Analysis Tool]的[!UICONTROL Admin Panel]中的*&#x200B;位置

1. 阅读&#x200B;*的*&#x200B;使用条款[!DNL Site-Wide Analysis Tool]并单击&#x200B;**[!UICONTROL Accept]**&#x200B;以继续。

   每个用户都必须接受会话的使用条款。 对于每个已登录的会话，将重复执行此步骤。


1. 在功能板顶部，单击要查看的选项卡。

   ![站点范围分析仪表板](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]信息*

## 从[!DNL Site-Wide Analysis Tool Dashboard]生成报告

1. 单击仪表板右上角的&#x200B;**[!UICONTROL Generate Report]**。

1. 选中要包含在报告中的每个&#x200B;**[!UICONTROL Type]**&#x200B;和&#x200B;**[!UICONTROL Priority]**&#x200B;设置的复选框。

1. 单击&#x200B;**[!UICONTROL Generate Report]**。

   ![站点范围分析仪表板](../../assets/tools/swat-report-settings.png)
   *报告设置*

| 选项卡 | 描述 |
| --- | --- |
| 仪表板 | 按优先级显示带有当前通知和建议的系统运行状况。 |
| 信息 | 提供客户联系信息和当前票证摘要，以及有关每个已安装Adobe Commerce产品的详细信息。 |
| Recommendations | 列出基于最佳实践的建议，以解决在您的网站上检测到的问题。 |
| 例外 | 列出由无错误处理程序的异常条件引起的应用程序引发的错误。 |
| 扩展 | 列出所有第三方扩展和第三方库。 |

>[!NOTE]
>
>应用推荐后，可能需要几天时间才能在[!DNL Site-Wide Analysis Tool Dashboard]或生成的报告中更新该推荐。
