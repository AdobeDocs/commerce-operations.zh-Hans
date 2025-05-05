---
title: ACSD-64149：仅编辑一个日期时，可以保存具有[!UICONTROL Date range]条件的客户区段
description: 应用ACSD-64149修补程序以修复Adobe Commerce问题，该问题导致在仅编辑其中一个日期时可以保存具有**[!UICONTROL Date range]**条件的客户区段。
feature: Customers, Admin Workspace
role: Admin, Developer
source-git-commit: c1c5256aee44ce65e9339cf3985e53f710fc7c8a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64149：仅编辑一个日期时，可以保存具有[!UICONTROL Date range]条件的客户区段

ACSD-64149修补程序修复了在仅编辑日期之一时可以保存具有日期范围条件的客户区段的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60时，此修补程序可用。 修补程序ID为ACSD-64149。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在编辑现有客户区段时，如果客户区段具有由日期范围指定的购物车内的产品的条件，则消费者`matchCustomerSegmentProcessor`将失败，并出现SQL错误。

<u>重现步骤</u>：

1. 确保使用者`matchCustomerSegmentProcessor`正在运行：

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. 转到&#x200B;**[!UICONTROL Magento backend]**。
1. 转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Segments]**。
1. 单击&#x200B;**[!UICONTROL Add Segment]**。
1. 输入&#x200B;**[!UICONTROL Segment Name]**，在&#x200B;**[!UICONTROL Assigned to Website]**&#x200B;下选择一个网站，并确保&#x200B;**[!UICONTROL Status]**&#x200B;设置为&#x200B;*活动*。
1. 单击&#x200B;**[!UICONTROL Save and Continue Edit]**。
1. 转到&#x200B;**[!UICONTROL Conditions]**&#x200B;选项卡并添加新条件： *产品{} > {}产品列表*{*}*。
1. 为&#x200B;**[!UICONTROL Date range]**&#x200B;添加子条件并设置有效的&#x200B;**[!UICONTROL Date range]**。
1. 单击&#x200B;**[!UICONTROL Date range]**&#x200B;旁边的绿色确认按钮。
1. 再次单击&#x200B;**[!UICONTROL Date range]**，选择日期选择器，编辑其中一个日期值，并单击绿色按钮进行确认。

<u>预期的结果</u>：

编辑时，**[!UICONTROL Date range]**&#x200B;选择器不应在日期中添加时间。

<u>实际结果</u>：

* **[!UICONTROL Date range]**&#x200B;选择器将时间添加到日期：
   * 一个日期仅具有日期，而另一个日期同时具有指定的日期和时间。
* 日志中显示以下错误：

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
