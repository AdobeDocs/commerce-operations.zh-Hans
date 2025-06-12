---
title: ACSD-48059：商家无法为“类别”属性保存[!UICONTROL Match product by rule]。
description: 应用ACSD-48059修补程序以修复Adobe Commerce问题，该问题导致商家无法保存“类别”属性的[!UICONTROL Match product by rule]。
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
exl-id: e156a752-81b3-4404-81e2-af7ed29f2b1d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-48059：商家无法保存类别属性的&#x200B;*[!UICONTROL Match product by rule]*

ACSD-48059修补程序修复了商家无法为[!DNL Visual Merchandiser]中的类别属性保存&#x200B;*[!UICONTROL Match product by rule]*&#x200B;的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-48059。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）>=2.3.7 &lt;2.4.7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

商家无法为[!DNL Visual Merchandiser]中的类别属性保存&#x200B;*[!UICONTROL Match product by rule]*。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]**，添加类别。
1. 转到Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**。
   * 转到[!UICONTROL Products in Category]部分。
   * 添加具有categories属性的新&#x200B;*[!UICONTROL Match products by rule]*&#x200B;条件。

<u>预期的结果</u>：

已成功保存类别。

<u>实际结果</u>：

* 无法使用新规则和条件保存类别。
* *保存类别时出错*&#x200B;错误显示。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
