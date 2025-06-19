---
title: ACSD-49835：未保存[!UICONTROL Use Default Value]复选框
description: 应用ACSD-49835修补程序以修复在多选属性的存储级别上未正确保存[!UICONTROL Use Default Value]复选框的Adobe Commerce问题。
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835：未保存[!UICONTROL Use Default Value]复选框

ACSD-49835修补程序修复了在多选属性的存储级别上未正确保存[!UICONTROL Use Default Value]复选框的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49835。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未在多选属性的存储级别上正确保存[!UICONTROL Use Default Value]复选框。

<u>重现步骤</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;中创建一个&#x200B;**[!UICONTROL Multiple-select Attribute]**&#x200B;并将其添加到属性集。
1. 转到&#x200B;**[!UICONTROL Product]**&#x200B;并在&#x200B;**[!UICONTROL All Store Views (Default Scope)]**&#x200B;中保存&#x200B;**[!UICONTROL Values]**。
1. 转到特定的&#x200B;**[!UICONTROL Store View Scope]**&#x200B;并保存产品。
1. 转到&#x200B;**[!UICONTROL Store View Scope]**&#x200B;并选中&#x200B;**[!UICONTROL Use Default Value]**&#x200B;复选框。

<u>预期的结果</u>：

选中[!UICONTROL Store View Scope]中的[!UICONTROL Use Default Value]复选框时，已正确保存多选属性值。

<u>实际结果</u>：

选中[!UICONTROL Store View Scope]中的[!UICONTROL Use Default Value]复选框时，未正确保存多选属性值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
