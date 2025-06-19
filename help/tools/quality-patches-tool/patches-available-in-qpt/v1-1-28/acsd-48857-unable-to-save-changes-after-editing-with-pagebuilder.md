---
title: ACSD-48857：使用 [!DNL Page Builder]编辑后无法保存更改
description: 应用ACSD-48857修补程序以修复使用 [!DNL Page Builder]编辑后用户无法保存更改的Adobe Commerce问题。
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-48857：使用[!DNL Page Builder]编辑后无法保存更改

ACSD-48857修补程序修复了用户使用[!DNL Page Builder]编辑后无法保存更改的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28时，此修补程序可用。 修补程序ID为ACSD-48857。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用[!DNL Page Builder]编辑之后，用户无法保存更改。

<u>重现步骤</u>

1. 登录到Admin网站。
1. 导航到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**&#x200B;以创建空的CMS页面。
1. 运行此SQL脚本以设置以下&#x200B;**[!UICONTROL Content]**&#x200B;字段值：

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. 在管理员中返回&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**。
1. 编辑您的页面。
1. 转到&#x200B;**[!UICONTROL Content]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>

HTML内容清理已实施。 这将删除文本编辑器生成的内容中的[!DNL Page Builder]保留HTML属性。

<u>实际结果</u>

页面保持未保存状态，加载器继续旋转。 在控制台中，生成以下错误：

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
