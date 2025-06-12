---
title: ACSD-46581：在购物车中选择国家/地区后，预计税额合计未更新
description: 应用ACSD-46581补丁以解决在购物车中切换国家/地区后税率未更新的Adobe Commerce问题。
feature: Orders, Shopping Cart
role: Admin
exl-id: 45800055-8556-4f87-8938-c6be5d82938d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-46581：在购物车中选择国家/地区后，预计税额合计未更新

此ACSD-46581补丁解决了在购物车中切换国家/地区后税率未更新的问题。 它仅在选择配送方式后更新。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21时，此修补程序可用。 修补程序ID为ACSD-46581。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在购物车中切换国家/地区后，税率不会更新。

<u>重现步骤</u>：

1. 在Adobe Commerce管理员中，转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**。
1. 为&#x200B;**[!UICONTROL Country]** = _美国_，**[!UICONTROL State]** = _*_，**[!UICONTROL Rate]** = _8.25_&#x200B;创建新的税率。
1. 为&#x200B;**[!UICONTROL Country]** = _印度_，**[!UICONTROL State]** = _*_，**[!UICONTROL Rate]** = _10_&#x200B;创建新的税率。
1. 创建包含美国和印度税率的税则。
1. 转到&#x200B;**[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]**&#x200B;并启用多个配送方式（例如&#x200B;_统一费率_&#x200B;和&#x200B;_免运费_）。
1. 使用&#x200B;**[!UICONTROL Taxable Goods]**&#x200B;税分类创建简单产品。
1. 将产品添加到商店前面的购物车。
1. 打开购物车并检查税额。
1. 将应用美国的默认税务设置，并按8.25%的税率计算税额。
1. 把国家换成印度。

<u>预期的结果</u>：

将该国改用印度时，税率改为10%。

<u>实际结果</u>：

在购物车的总部分中，税额保持不变。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中可用的其他修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
