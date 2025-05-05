---
title: ACSD-63454：下拉列表和多选属性的默认值未正确保存在数据库中
description: 应用ACSD-63454修补程序以修复Adobe Commerce问题，该问题导致下拉列表和多选属性的默认值未正确保存在数据库中。
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
source-git-commit: cb73a5a346ec0e8acd59accf73605e25ef35c3ca
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454：数据库中未正确保存[!UICONTROL Dropdown]和[!UICONTROL Multiple Select]属性的默认值

ACSD-63454修补程序修复了[!UICONTROL Dropdown]和[!UICONTROL Multiple Select]属性的默认值在数据库中未正确保存的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-63454。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!UICONTROL Dropdown]和[!UICONTROL Multiple Select]属性的默认值在数据库中未正确保存；新值将被附加到旧值，并以逗号分隔，而不是更新默认值。

<u>重现步骤</u>：

1. 登录到后端，转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**。
1. 单击&#x200B;**[!UICONTROL Add New Attribute]**。
1. 在&#x200B;**[!UICONTROL Properties]**&#x200B;选项卡中，设置以下内容：
   * **[!UICONTROL Default Label]**： *测试*
   * **[!UICONTROL Catalog Input Type for Store Owner]**： *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**：添加两个选项而不选择&#x200B;**[!UICONTROL Is Default]**。
1. 单击&#x200B;**[!UICONTROL Save Attribute]**。
1. 在数据库中检查`default_value`列是否为空。

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. 返回并将两个选项之一设置为&#x200B;**[!UICONTROL Is Default]**。
1. 再次检查数据库以确保`default_value`现在包含所选的选项ID。
1. 返回并通过选择另一个选项来更改默认选项。

<u>预期的结果</u>：

新的默认值应取代数据库中的旧值。

<u>实际结果</u>：

它不会将默认值替换为新值，而是将新值附加到旧值，并以逗号分隔。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
