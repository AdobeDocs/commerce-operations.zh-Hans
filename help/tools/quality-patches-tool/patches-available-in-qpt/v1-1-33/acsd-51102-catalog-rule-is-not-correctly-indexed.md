---
title: ACSD-51102：应用于大量产品的目录规则未正确编制索引
description: 应用ACSD-51102修补程序以修复Adobe Commerce问题：当计划更新启用了应用于大量产品的目录规则时，该规则无法正确编制索引。
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102：应用于大量产品的目录规则未正确编制索引

ACSD-51102修补程序修复了以下问题：当计划更新启用了应用于大量产品的目录规则时，该规则无法正确编制索引。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51102。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

计划更新启用了应用于大量产品的目录规则时，该规则无法正确编制索引。

先决条件：

* Cron作业已设置并每分钟运行一次。

<u>重现步骤</u>：

1. 创建一个包含数千个产品的大型目录，以便在启用目录规则时，使&#x200B;*目录规则*&#x200B;索引器的运行时间超过120秒。
2. 创建两个将&#x200B;*活动*&#x200B;状态设置为&#x200B;*否*&#x200B;的目录规则。  例如，*Test 1*&#x200B;和&#x200B;*Test 2*。 每个规则都应影响目录中的所有产品，并导致索引器运行超过120秒。
3. 确保索引器的状态为&#x200B;*就绪*。
4. 创建计划更新以启用这两个规则。 *测试2*&#x200B;计划应在&#x200B;*测试1*&#x200B;后不久开始。 例如，差异为1分钟。
5. 检查店面的产品价格。

<u>预期的结果</u>

将应用这两个规则的折扣。

<u>实际结果</u>

仅应用第一个规则折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
