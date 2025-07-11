---
title: ACSD-56546：可配置和捆绑产品在店面显示为缺货
description: 应用ACSD-56546修补程序以修复在禁用*[!UICONTROL Display Out of Stock Products]*配置选项时，可配置和捆绑产品在店面显示为缺货的Adobe Commerce问题。
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-56546：可配置和捆绑产品在店面显示为缺货

ACSD-56546修补程序修复了可配置和捆绑产品在店面显示为缺货的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48时，此修补程序可用。 修补程序ID为ACSD-56546。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

禁用&#x200B;*[!UICONTROL Display Out of Stock Products]*&#x200B;选项时，可配置和捆绑产品在店面显示为缺货。

<u>重现步骤</u>：

1. 将&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;选项设置为&#x200B;*否*。
1. 创建网站、商店和商店评论。
1. 创建源和库存，然后将其分配给第二个网站。
1. 创建具有两个子产品的&#x200B;*可配置产品*。 将子产品同时分配给源和两个网站。
1. 更新第一个子产品，使两个源中的&#x200B;*qty=0*。
1. 更新第二个子产品并在第二个网站上禁用它。
1. 执行完整的重新索引。
1. 选中第二个网站上包含可配置产品的类别。

<u>预期的结果</u>：

缺货的可配置产品在店面不可见。

<u>实际结果</u>：

即使&#x200B;*[!UICONTROL Display Out of Stock Products]*&#x200B;选项被禁用，缺货的可配置产品在店面中仍可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
