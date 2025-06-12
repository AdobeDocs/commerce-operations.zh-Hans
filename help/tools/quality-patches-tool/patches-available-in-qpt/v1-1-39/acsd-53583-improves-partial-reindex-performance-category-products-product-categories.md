---
title: ACSD-53583：改进[!UICONTROL Category Products]和[!UICONTROL Product Categories]索引器的部分重新索引性能
description: 应用ACSD-53585补丁程序，以提高“类别产品”和“产品类别”索引器的部分重新索引性能。
feature: Products, Categories
role: Admin, Developer
exl-id: 11e60cc2-1f7e-4e4a-a5eb-0f1dbe399ef2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-53583：提高类别产品和产品类别索引器的部分重新索引性能

ACSD-53583修补程序改进了&#x200B;*类别产品*&#x200B;和&#x200B;*产品类别*&#x200B;索引器的部分重新索引性能。 安装[!DNL Quality Patches Tool (QPT)] 1.1.39时，此修补程序可用。 修补程序ID为ACSD-53583。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3
* 与[!DNL Live Search]模块不兼容。 为了将此修补程序应用于[!DNL Live Search]安装，请请求一个额外的ACSD-55719修补程序。

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

部分重新索引比完全重新索引花费的时间长。

<u>重现步骤</u>：

1. 将所有索引器转换为&#x200B;*按计划*&#x200B;更新。
1. 使用[!DNL Performance Toolkit] （中型配置文件）生成数据。
1. 对所有产品和类别进行更改，以使它们位于索引积压中，并且所有索引都处于空闲状态。
1. 对&#x200B;*类别产品*&#x200B;和&#x200B;*产品类别*&#x200B;索引器执行部分重新索引。

<u>预期的结果</u>：

由于所有产品和类别都已更改，因此每个产品会调用一次部分重新索引，所用时间与完全重新索引几乎相同。

<u>实际结果</u>：

每个产品会多次调用部分重新索引，其所用时间比完全重新索引要长。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
