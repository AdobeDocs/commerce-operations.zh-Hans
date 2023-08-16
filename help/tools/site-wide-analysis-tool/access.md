---
title: 如何访问 [!DNL Site-Wide Analysis Tool]
description: 了解如何访问 [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# 如何访问 [!DNL Site-Wide Analysis Tool]

您可以通过两种方式访问 [!DNL Site-Wide Analysis Tool Dashboard].

您可以访问 [!DNL dashboard] 从 [[!DNL Site-Wide Analysis Tool] 网站](https://supportinsights.adobe.com/commerce) 直接 **(仅适用于Adobe Commerce云基础架构)** 并使用Adobe ID登录，或通过 [!DNL dashboard] 从您商店的 [!DNL Admin Panel].

此 [!DNL Site-Wide Analysis Tool] 服务在以下位置提供： [生产模式](https://docs.magento.com/user-guide/magento/installation-modes.html) 对象 [!DNL Admin] 有权访问用户的用户 [角色资源](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>如果您内部安装了Adobe Commerce，则必须安装 [代理](../site-wide-analysis-tool/installation.md) ，以便使用该工具。

![站点范围分析功能板](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]仪表板*

## 选项1：登录到您的 [!DNL Site-Wide Analysis Tool Dashboard] 直接从 [!DNL Site-Wide Analysis Tool] 域(仅适用于云基础架构上的Adobe Commerce)

An **[!DNL Adobe ID]为必填项** 访问 [!DNL Commerce] 帐户。
如果您已经拥有 [!DNL Commerce] 帐户，但您没有 [!DNL Adobe ID]，您可以在登录过程中创建一个。

1. 转到 [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. 单击 **[!UICONTROL Sign in with Adobe ID]** 按钮并按照提示操作。

   ![站点范围分析功能板](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]登录屏幕*

1. 接受条款和条件。

1. **<u>注意</u>：** 您的帐户应有权访问 **[!DNL Support Permissions]** 以访问 [!DNL Site-Wide Analysis Tool Dashboard].
欲知更多详情，请参阅 [共享 [!DNL Commerce] 帐户](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) 在我们的用户指南中。

## 选项2：登录到您的 [!DNL Site-Wide Analysis Tool Dashboard] 从您商店的 [!DNL Admin Panel]

### 步骤1：验证权限

验证 [!DNL Admin] 用户帐户具有访问 [!DNL Site-Wide Analysis Tool] 通过 [已分配的用户角色](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>此 [!DNL Site-Wide Analysis Tool] 角色资源（权限）是 **非** 自动分配。 必须为中的用户角色和单独分配给每个用户帐户的角色激活该角色。 [!UICONTROL Admin].

对于需要的自定义角色 [!DNL Site-Wide Analysis Tool] 访问，请执行以下操作：

1. 选择 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 角色资源。

   ![站点范围分析功能板](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]为角色选择的权限*

1. 单击 **[!UICONTROL Save Role]**.

1. 通知所有分配了该角色的用户注销 [!DNL Admin]，然后重新登录。

>[!NOTE]
>
>如果您已验证用户帐户具有访问 [!DNL Site-Wide Analysis Tool] 并且用户尝试从访问工具时收到403错误 [!DNL Admin]，则云基础架构上的Adobe Commerce实例可能已启用HTTP访问控制。 此 [!DNL Site-Wide Analysis Tool] 如果您启用了HTTP身份验证，则不支持仪表板。 有关解决此问题的更多信息，请参阅我们的 [支持文章](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### 步骤2：访问 [!DNL Site-Wide Analysis Tool]

1. 在 *[!UICONTROL Admin]* 侧栏，转到 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![站点范围分析功能板](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]中的位置 [!DNL Admin Panel] 在Adobe Commerce中*

1. 阅读 *使用条款* 对于 [!DNL Site-Wide Analysis Tool] 并单击 **[!UICONTROL Accept]** 以继续。

   每个用户都必须接受会话的使用条款。 对于每个已登录的会话，将重复执行此步骤。


1. 在功能板顶部，单击要查看的选项卡。

   ![站点范围分析功能板](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]信息*

## 从生成报表 [!DNL Site-Wide Analysis Tool Dashboard]

1. 在仪表板的右上角，单击 **[!UICONTROL Generate Report]**.

1. 选中每个的复选框 **[!UICONTROL Type]** 和 **[!UICONTROL Priority]** 要包含在报告中的设置。

1. 单击 **[!UICONTROL Generate Report]**.

   ![站点范围分析功能板](../../assets/tools/swat-report-settings.png)
   *报表设置*

| 选项卡 | 描述 |
| --- | --- |
| 仪表板 | 按优先级显示带有当前通知和建议的系统运行状况。 |
| 信息 | 提供客户联系信息和当前票证摘要，以及有关每个已安装Adobe Commerce产品的详细信息。 |
| Recommendations | 列出基于最佳实践的建议，以解决在您的网站上检测到的问题。 |
| 例外 | 列出由无错误处理程序的异常条件引起的应用程序引发的错误。 |
| 扩展 | 列出所有第三方扩展和第三方库。 |

>[!NOTE]
>
>应用推荐后，可能需要几天时间才能在 [!DNL Site-Wide Analysis Tool Dashboard] 或生成的报告。
