---
title: 'ACSD-46815：使用紧凑策略部署静态内容失败'
description: 应用ACSD-46815修补程序以修复在使用压缩策略时静态内容部署失败的Adobe Commerce问题。
feature: Deploy, Page Content, SCD
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-46815：使用紧凑策略时，静态内容部署失败

ACSD-46815修补程序修复了使用压缩策略时静态内容部署失败的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20时，此修补程序可用。 修补程序ID为ACSD-46815。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用紧凑策略进行部署时，静态内容部署失败。

<u>重现步骤</u>：

1. 通过运行以下命令，使用压缩策略部署静态内容：

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>预期的结果</u>：

静态内容部署已完成，并且没有错误。

<u>实际结果</u>：

静态内容部署因紧凑策略而失败。 在部署过程中出现以下错误： *来自/app/pub/static/adminhtml/debugger/base/default/的Magento。无法读取/node_modules/@spectrum-css/vars/dist/spectrum-global.css文件。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
