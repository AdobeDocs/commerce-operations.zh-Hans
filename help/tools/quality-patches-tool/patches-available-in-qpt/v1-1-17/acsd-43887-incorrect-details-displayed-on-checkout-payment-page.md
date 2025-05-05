---
title: 'ACSD-43887：结账付款页面上显示的详细信息不正确'
description: ACSD-43887修补程序修复了在启用公司的采购订单时，在结账付款页面上显示不正确的详细信息的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17后，即可使用此修补程序。 修补程序ID为ACSD-43887。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# ACSD-43887：结账付款页面上显示的详细信息不正确

ACSD-43887修补程序修复了在启用公司的采购订单时，在结账付款页面上显示不正确的详细信息的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17时，此修补程序可用。 修补程序ID为ACSD-43887。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用公司的采购订单时，结帐付款页面上显示的详细信息不正确。

<u>先决条件</u>：

1. 已安装B2B模块。
1. 启用公司设置为&#x200B;_是_。 转到&#x200B;**商店** > **配置** > **常规** > **B2B功能** > **启用公司** > **是**。
1. 启用采购订单设置为&#x200B;_是_。 转到&#x200B;**订单审批配置** > **启用采购订单** > **是**。
1. 将PayPal Express配置为付款方式。

<u>重现步骤</u>：

1. 创建虚拟产品。
1. 从前端向公司管理员注册公司帐户。
1. 批准来自后端的公司帐户，并在批准公司时将&#x200B;**启用采购订单**&#x200B;设置为&#x200B;_是_。
1. 转到前端，然后使用在步骤2中创建的公司管理员帐户登录。
1. 为公司创建“默认用户”。 转到&#x200B;**公司用户** > **添加新用户**。
1. 为公司创建“批准规则”。 转到&#x200B;**审批规则** > **添加新规则**。

   * 规则类型：订单合计
   * 订单合计：大于或等于$1
   * 需要获得以下审批：公司管理员

1. 注销并使用“Default User”帐户登录。
1. 将步骤1中创建的虚拟产品添加到购物车并继续结帐。
1. 选择PayPal Express作为付款方式，然后单击&#x200B;**下达采购订单**。
1. 注销并使用公司管理员帐户登录。
1. 转到&#x200B;**我的采购订单**，在&#x200B;**公司采购订单**&#x200B;中，单击在步骤9中创建的订单的&#x200B;**查看**。
1. 审批采购订单。 采购订单状态应为“Approved： Pending Payment”（已批准：待定付款）。
1. 注销并使用公司“默认用户”帐户登录。
1. 转到&#x200B;**我的采购订单** > **查看** > **下订单**。
1. 检查&#x200B;**订单摘要**。

<u>预期的结果</u>：

订单摘要显示正确的非零值。

<u>实际结果</u>：

订单汇总合计值为零。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
