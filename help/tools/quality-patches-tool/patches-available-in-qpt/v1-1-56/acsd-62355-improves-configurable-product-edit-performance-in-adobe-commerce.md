---
title: ACSD-62355：提高Adobe Commerce中可配置产品的编辑性能
description: 应用ACSD-62355修补程序以修复Adobe Commerce问题：当产品基于许多具有许多值的属性时，该问题会导致可配置产品编辑页面加载缓慢。
feature: Admin Workspace
role: Admin, Developer
source-git-commit: e8694744c8a2411a8e966148860f43fb56b48772
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355：提高Adobe Commerce中可配置产品的编辑性能

当产品具有许多值众多的属性时，ACSD-62355修补程序修复了可配置产品编辑页面上加载时间缓慢和内存消耗高的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-62355。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当可配置产品基于具有多个值的多个属性时，可配置产品编辑页面需要很长时间才能加载，从而导致延迟以及潜在的超时或内存限制问题。

<u>重现步骤</u>：

1. 在默认属性集中创建9个新属性，每个属性都是[!UICONTROL Filterable]并具有[!UICONTROL Scope]： [!UICONTROL Global]。
   * 属性1:50个选项
   * 属性2:20个选项
   * 属性3:10个选项
   * 属性4:5个选项
   * 属性5:5个选项
   * 属性6:5个选项
   * 属性7:5个选项
   * 属性8:3个选项
   * 属性9:2个选项

1. 通过新创建的属性的选项组合，创建9个简单的产品。
   * 产品1：每个属性的第一个选项
   * 产品2：每个属性的第二个选项
   * 产品3：每个属性的第三个选项
   * 产品4：每个属性的第四个选项
   * 如果属性的选项数少于产品数，请将剩余的产品分配给该属性中的随机选项。

1. 创建使用新创建属性的可配置产品：
   * 使用以下配置添加一个子产品：
      * 使用“属性1”中的最后一个选项，以及“属性2”到“属性9”中的第一个选项。
      * 这将生成1个可配置产品和1个子产品。
1. 转到可配置产品的&#x200B;**[!UICONTROL Configurations]**&#x200B;选项卡。
1. 手动单击&#x200B;**[!UICONTROL Add Products]**&#x200B;并开始逐一添加以前创建的简单产品。
1. 每次添加后保存更改。
1. 添加产品时，请观察编辑可配置产品页面的加载时间。
1. 添加7个产品后，您应该会注意到RAM消耗和页面加载时间显着增加

<u>预期的结果</u>：

产品编辑表单应快速高效地加载，且不会造成过多的内存消耗。

<u>实际结果</u>：

编辑可配置产品需要很长时间才能加载，并且可能会达到内存限制或超时错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
