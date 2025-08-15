---
title: ACSD-51114：启用异步索引后，随机产品从大型目录中消失
description: 应用ACSD-51114修补程序以修复Adobe Commerce问题。启用异步索引后，大型目录中随机产品消失。
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51114：启用异步索引后，随机产品从大型目录中消失

>[!NOTE]
>
>此修补程序已弃用。

ACSD-51114修补程序修复了在启用异步索引后，随机产品从大型目录中消失的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30时，此修补程序可用。 修补程序ID为ACSD-51114。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`程序包更新到最新版本，并在[[!DNL Quality Patches Tool]:Search修补程序页面上进行兼容性检查。将修补程序ID用作搜索关键字来查找修补程序。

## 问题

启用异步索引后，随机产品从大型目录中消失。

<u>重现步骤</u>：

1. 创建一组10个产品。
1. 将所有索引器设置为&#x200B;**[!UICONTROL Update on Save]**&#x200B;模式。
1. 创建一个类别并将所有产品分配给该类别。
1. 禁用所有产品。
1. 打开类别并验证那里没有产品。
1. 将所有索引器设置为&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;模式。
1. 在`DEFAULT_BATCH_SIZE`中将`lib/internal/Magento/Framework/Mview/View.php#L31`设置为2。
1. 按照以下顺序启用产品：1、9、2、5、10、3。
1. 运行cron命令。
1. 再次打开类别。

<u>预期的结果</u>：

将显示所有启用的产品。

<u>实际结果</u>：

未显示所有启用的产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
