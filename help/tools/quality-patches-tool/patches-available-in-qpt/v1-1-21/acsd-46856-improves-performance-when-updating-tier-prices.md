---
title: ACSD-46856：在更新层价格时提高性能
description: 应用ACSD-46856补丁程序，以便在通过System &amp；Configuration &amp；gt； Import &amp；gt； Advanced Pricing更新层价格时提高性能。
feature: Orders
role: Admin
exl-id: 5c954f2c-a55c-43ba-919f-406f4b173d30
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-46856：通过系统>配置>导入>高级定价更新层价格缓慢

ACSD-46856修补程序在通过&#x200B;**[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]**&#x200B;更新层价格时提高了性能。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21时，此修补程序可用。 修补程序ID为ACSD-46856。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过&#x200B;**[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]**&#x200B;更新层价格的速度较慢。

<u>重现步骤</u>：

* 通过&#x200B;**系统** > **配置** > **导入** > **高级定价**&#x200B;导入大量产品（例如：10k+或200k+）。

<u>预期的结果</u>：

使用该修补程序，200,000多种产品的处理时间约为1:00分钟。

<u>实际结果</u>：

如果没有该修补程序，1万多个产品的处理时间大约为10:00分钟。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
