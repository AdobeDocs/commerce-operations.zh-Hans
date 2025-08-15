---
title: ACSD-46618：产品列表构件显示已登录客户的不正确缓存价格
description: 应用补丁以修复Adobe Commerce问题，该问题导致产品列表构件为登录客户显示不正确的缓存价格。
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-46618：产品列表构件显示已登录客户的不正确缓存价格

ACSD-46618修补程序解决了产品列表构件为已登录的客户显示不正确的缓存价格的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html?lang=zh-Hans) 1.1.21时，此修补程序可用。 修补程序ID为ACSD-46618。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

ACSD-46618修补程序解决了产品列表构件为已登录的客户显示不正确的缓存价格的问题。

<u>重现步骤</u>：

1. 在Adobe Commerce Admin中，选择&#x200B;**[!UICONTROL Stores]**，然后选择&#x200B;**[!UICONTROL Configuration]**，展开&#x200B;**[!UICONTROL Sales]**，然后选择&#x200B;**[!UICONTROL Tax]**。 更新税设置以显示含税和不含税的价格。
1. 设置&#x200B;**[!UICONTROL Enable Cross Border Trade]** = _是_。
1. 创建一个仅适用于美国的税则。
1. 向主页添加一个包含多个产品的构件。
1. 创建两个具有美国地址和非美国地址的客户。
1. 从店面使用美国客户登录。 确保已缓存页面。
1. 观察主页小部件中显示的价格。
1. 注销并使用非美国客户登录。

<u>预期的结果</u>：

主页小组件中显示的价格对应于客户的地址。

<u>实际结果</u>：

主页小组件显示针对非美国客户使用该税的价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中可用的其他修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
