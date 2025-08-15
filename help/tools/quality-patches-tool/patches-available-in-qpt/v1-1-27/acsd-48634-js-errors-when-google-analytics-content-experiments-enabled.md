---
title: ACSD-48634：启用 [!DNL JS] 时出现 [!DNL Google Analytics Content Experiments] 错误
description: 启用 [!DNL JS] 时，应用ACSD-48634修补程序以修复 [!DNL staging] 更新页面上的 [!DNL Google Analytics Content Experiments] 错误。
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634：启用[!DNL JS]时出现[!DNL Google Analytics Content Experiments]错误

启用[!DNL JS]后，ACSD-48634修补程序修复了[!DNL staging]更新页面上的[!DNL Google Analytics Content Experiments]错误。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-48634。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用[!DNL JS]后，[!DNL staging]更新页面上出现[!DNL Google Analytics Content Experiments]错误。

<u>重现步骤</u>：

1. 在&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;中，创建其他网站、商店和&#x200B;**[!UICONTROL Store View]**。 确保&#x200B;**[!UICONTROL Store View]**&#x200B;为&#x200B;*[!UICONTROL Enabled]*。
1. 通过转至&#x200B;**[!DNL Configure Google Analytics]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]**&#x200B;配置&#x200B;**[!UICONTROL Google API]**：
   * 对于&#x200B;**[!DNL Main]**&#x200B;和其他网站[!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**： *[!UICONTROL (GTM container ID)]*
      * 其他字段的&#x200B;**[!DNL Uncheck]** *[!UICONTROL Use Default]*，但不更改它们。
   * 对于&#x200B;**[!DNL Default Config]** [!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**： *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
1. 通过将&#x200B;**[!DNL Configure Google Analytics]**&#x200B;从&#x200B;**[!DNL Default Config]**&#x200B;更改为[!DNL scope]，禁用&#x200B;**[!UICONTROL Enable]** *[!UICONTROL Yes]*&#x200B;上的&#x200B;*[!UICONTROL No]*。 确保不更改其他任何内容！
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**。
1. 创建并编辑任何&#x200B;**[!UICONTROL category]**&#x200B;并为其添加计划更新：
   * 任何名称、将来的开始日期、将来的结束日期以及&#x200B;**[!UICONTROL category]**&#x200B;中的任何更改([!UICONTROL For Example]： *[!UICONTROL disable category]*)。
1. 保存更新并检查[!DNL browser developer console]是否有错误。

<u>预期的结果</u>：

没有[!DNL JS]错误，对[!DNL staging]更新的更改已成功保存。

<u>实际结果</u>：

控制台中显示[!DNL JS]个错误，表单格式不正确，保存后[!DNL spinner]从未被禁用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
