---
title: ACSD-65127：生产模式中的JavaScript缩小导致浏览器中出现 [!DNL TinyMCE] 6错误
description: 应用ACSD-65127修补程序以修复Adobe Commerce问题，该问题导致在生产模式下启用JavaScript缩小导致 [!DNL TinyMCE] 6在浏览器控制台中生成错误，从而影响功能和用户体验。
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-65127：生产模式中的JavaScript缩小导致浏览器中出现[!DNL TinyMCE] 6错误

ACSD-65127修补程序修复了在生产模式下启用JavaScript缩小导致[!DNL TinyMCE] 6在浏览器控制台中生成错误，从而影响功能和用户体验的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACSD-65127。 请注意，此问题已在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)页面上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在生产模式下启用JavaScript缩小会导致[!DNL TinyMCE] 6在浏览器控制台中生成错误，从而影响功能和用户体验。

<u>重现步骤</u>：

1. 通过运行以下命令来设置配置：

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. 启用生产模式。

```
bin/magento deploy:mode:set production
```

1. 在管理员侧边栏上，转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。 单击任何列出的产品上的&#x200B;**[!UICONTROL Edit]**，向下滚动到&#x200B;**[!UICONTROL Content]**&#x200B;并选择&#x200B;**[!UICONTROL Show Editor]**。

<u>预期的结果</u>：

浏览器控制台中没有JS错误。

<u>实际结果</u>：

js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`的浏览器控制台中出现&#x200B;*404*&#x200B;错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
