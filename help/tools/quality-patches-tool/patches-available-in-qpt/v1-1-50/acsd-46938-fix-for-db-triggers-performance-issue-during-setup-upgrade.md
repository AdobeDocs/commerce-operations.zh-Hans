---
title: ACSD-46938：在“setup：upgrade”期间数据库触发器出现性能问题
description: 应用ACSD-46938修补程序以修复Adobe Commerce问题，该问题导致“setup：upgrade”命令将索引器模式从计划更改为保存，从而显着降低性能。
feature: Upgrade
role: Admin, Developer
exl-id: a4e88329-c5bb-4666-8738-b78b86056b71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-46938：在`setup:upgrade`期间数据库触发器出现性能问题

ACSD-46938修补程序修复了`setup:upgrade`命令将索引器模式从计划更改为保存，从而导致性能显着下降的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-46938。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在`setup:upgrade`中重新创建DB触发器期间性能下降。

<u>重现步骤</u>：

1. 创建一个包含许多产品和类别的大型目录。
1. 登录到[!UICONTROL Admin]。
1. 将所有索引器设置为[!UICONTROL Update By Schedule]模式。
1. 打开任何产品。
1. 更新它。 例如，为其分配一个新类别。
1. 单击[!UICONTROL Save]。
1. 并行运行`bin/magento setup:upgrade`和`bin/magento cron:run`命令。

<u>预期的结果</u>：

同时执行`bin/magento setup:upgrade`命令时，`bin/magento cron:run`命令的执行时间会显着增加。

<u>实际结果</u>：

命令的执行时间不会增加。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
