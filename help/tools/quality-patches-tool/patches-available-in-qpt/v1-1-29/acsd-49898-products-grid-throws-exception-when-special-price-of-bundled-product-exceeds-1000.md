---
title: ACSD-49898：产品网格引发异常
description: 应用ACSD-49898修补程序以修复捆绑产品的特殊价格超过1000时，产品网格会引发异常的Adobe Commerce问题。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: adc8f12e-73e4-4ed5-8081-a9907ec13342
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-49898：产品网格引发异常

ACSD-49898修补程序修复了捆绑产品的特殊价格超过1000时，产品网格引发异常的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49898。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当捆绑产品的特殊价格超过1000时，产品网格会引发异常。 该问题与在某些区域设置中使用逗号而不是点来表示小数有关。

<u>重现步骤</u>：

1. 创建捆绑产品。
1. 将特价设为9999，保存并关闭。
1. 导航到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>搜索捆绑产品SKU（如果不可见）。

<u>预期的结果</u>：

* 用户能够过滤/查看捆绑产品的特价。
* 对于捆绑产品，特殊价格以百分比显示；对于其他产品类型，特殊价格以价格显示。

<u>实际结果</u>：

引发以下错误： *遇到非数字值*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
