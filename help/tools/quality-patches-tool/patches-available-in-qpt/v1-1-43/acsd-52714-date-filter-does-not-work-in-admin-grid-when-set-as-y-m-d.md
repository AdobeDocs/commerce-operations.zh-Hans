---
title: ACSD-52714：将日期过滤器设置为y-m-d时，该过滤器在管理网格中不起作用
description: 应用ACSD-52714修补程序以修复将日期格式设置为y-m-d时，日期过滤器在管理网格中不起作用的Adobe Commerce问题。
feature: Attributes
role: Admin, Developer
exl-id: 4a34900b-9566-41bb-8d3e-18a440117907
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-52714：将日期过滤器设置为y-m-d时，该过滤器在管理网格中不起作用

ACSD-52714修补程序修复了将日期格式设置为y-m-d时，日期过滤器在管理网格中不起作用的问题。安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43时，此修补程序可用。 修补程序ID为ACSD-52714。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将日期格式设置为y-m-d时，日期过滤器在管理网格中不起作用。

<u>重现步骤</u>：

1. 安装干净的Adobe Commerce。
1. 编辑
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
文件并添加
   `<dateFormat>Y-MM-dd</dateFormat>`
到
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
在标记下
   `<dataType>date</dataType>`

1. 刷新缓存`bin/magento c:f`。
1. 登录到管理员并从&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;创建新客户。

   * 起始日期：当前日期减1天
   * 截止日期：当前日期

1. 单击&#x200B;**[!UICONTROL Apply Filters]**。

<u>预期的结果</u>：

网格的日期过滤器工作正常，与区域设置无关。

<u>实际结果</u>：

出现以下消息： *我们找不到任何记录*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
