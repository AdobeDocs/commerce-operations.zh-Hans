---
title: ACSD-56246：计划产品更新将清除多选属性值
description: 应用ACSD-56246修补程序以修复Adobe Commerce问题，该问题导致安排产品更新时清除多选属性值。
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56246：计划产品更新将清除多选属性值

ACSD-56246修补程序修复了计划产品更新时清除多选属性值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44时，此修补程序可用。 修补程序ID为ACSD-56246。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

计划的产品更新将清除多选属性值。

<u>重现步骤</u>：

1. 安装Adobe Commerce。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;并创建以下属性：

   * 默认标签：项目
   * 商店所有者的目录输入类型：多选
   * 管理选项（属性的值）：Choice、Sunscape、Safetyshield
   * 属性代码：customer_program
   * 范围：全局
   * 添加到列选项：否
   * 在筛选器选项中使用：否
   * 店面属性
   * 位置： *333*
   * 允许Storefront上的HTML标签：否

1. 运行
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`。
1. 运行
   `bin/magento setup:upgrade`。
1. 转到&#x200B;**[!UICONTROL Admin]** >选择任何简单产品>选择项目属性中的所有项目>单击&#x200B;**[!UICONTROL Save the product]**。
1. 安排在下一分钟更新此产品，并运行以下命令以使内容暂存正常运行：
   `for i in {1..100}; do bin/magento cron:run; done`。

<u>预期的结果</u>：

产品的&#x200B;**[!UICONTROL program]**&#x200B;属性不应更改。

<u>实际结果</u>：

产品的&#x200B;**[!UICONTROL program]**&#x200B;属性已被清除。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
