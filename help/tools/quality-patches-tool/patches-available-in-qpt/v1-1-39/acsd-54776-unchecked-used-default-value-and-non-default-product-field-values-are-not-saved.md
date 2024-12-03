---
title: ACSD-54776：未选中[!UICONTROL Use Default Value]，第二个网站、商店和商店视图不会保存非默认的产品字段值
description: 应用ACSD-54776修补程序以修复Adobe Commerce问题，该问题导致第二个网站、商店和商店视图未保存未勾选的[!UICONTROL Use Default Value]和非默认产品字段值。
feature: Products
role: Admin, Developer
exl-id: d9f63abb-5d00-4777-a186-1120344af018
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-54776：未选中&#x200B;*[!UICONTROL Use Default Value]*，并且不保存非默认的产品字段值

>[!NOTE]
>
>此修补程序取代了QPT 1.1.35中发布的[ACSD-51984](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md)修补程序。

ACSD-54776修补程序修复了未为第二个网站、商店和商店视图保存未勾选的&#x200B;**[!UICONTROL Use Default Value]**&#x200B;和非默认产品字段值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39时，此修补程序可用。 修补程序ID为ACSD-54776。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p4、2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于第二个网站、商店和商店视图，未选中&#x200B;*[!UICONTROL Use Default Value]*&#x200B;且未保存非默认产品字段值。

<u>重现步骤</u>：

1. 转到后端并导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL All Stores]**，然后创建新网站、商店和商店视图。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**，创建一个简单产品并保存它，然后从&#x200B;**[!UICONTROL Product in Websites]**&#x200B;将该产品分配给两个网站。
1. 从步骤2将范围更改为新创建的存储视图。
1. 转到&#x200B;**[!UICONTROL Search Engine Optimization]**&#x200B;并取消选中[!UICONTROL Meta Title]、[!UICONTROL Meta Keywords]和[!UICONTROL Meta Description]的&#x200B;**[!UICONTROL Use Default Value]**&#x200B;复选框。
1. 清除字段&#x200B;*[!UICONTROL Meta Title]*、*[!UICONTROL Meta Keywords]*&#x200B;和&#x200B;*[!UICONTROL Meta Description]*&#x200B;中的文本，然后单击&#x200B;**[!UICONTROL Save]**。
1. 再次转到&#x200B;**[!UICONTROL Search Engine Optimization]**。

<u>预期的结果</u>

将保存字段和复选框的值。

<u>实际结果</u>

未保存字段和复选框的值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](</help/tools/quality-patches-tool/usage.md>)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
