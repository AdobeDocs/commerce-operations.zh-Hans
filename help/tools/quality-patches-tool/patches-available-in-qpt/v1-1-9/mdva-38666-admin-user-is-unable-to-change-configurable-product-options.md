---
title: MDVA-38666：管理员用户无法更改可配置的产品选项
description: MDVA-38666修补程序解决了管理员用户无法更改客户购物车中可配置的产品选项的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-38666。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Admin Workspace, Configuration, Products
role: Admin
exl-id: 8e72f6a4-b36f-4fe4-bc01-2254984dd512
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-38666：管理员用户无法更改可配置的产品选项

MDVA-38666修补程序解决了管理员用户无法更改客户购物车中可配置的产品选项的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9时，此修补程序可用。 修补程序ID为MDVA-38666。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员用户无法更改客户购物车中的可配置产品选项。

<u>重现步骤</u>：

1. 将客户帐户范围设置为全局。
1. 使用商店创建两个网站。
1. 创建两个可配置的产品并将它们分配给每个网站。
1. 在前端创建客户帐户并登录。
1. 将产品添加到购物车并执行结账（此操作可使每个网站上的报价ID不同）。
1. 将产品添加到购物车中并保留它。
1. 切换到第二个网站并将产品添加到购物车（相同的登录应该有效，因为客户帐户范围设置为“全局”）。
1. 从管理员中打开客户并导航到购物车选项卡。
1. 从下拉列表中切换存储，然后尝试更改配置。

<u>预期的结果</u>：

用户会看到一个包含可配置选项的弹出窗口。

<u>实际结果</u>：

不显示弹出窗体。 用户无法更改配置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
