---
title: MDVA-41631：检索没有可选“电话”值的订单信息时出错
description: MDVA-41631修补程序修复了以下问题：用户通过 [!DNL GraphQL]检索订单信息时出现错误，且没有可选的“电话”值。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
source-git-commit: 3f14d93eca09967e320aae4af5e94c6d0c16cd20
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631：检索没有可选“电话”值的订单信息时出错

MDVA-41631修补程序修复了以下问题：用户通过[!DNL GraphQL]检索订单信息时出现错误，且没有可选的“电话”值。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7时，此修补程序可用。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过[!DNL GraphQL]检索订单信息时，用户在没有可选“电话”值的情况下收到错误。

<u>重现步骤</u>：

1. 前往&#x200B;**商店** > **配置** > **客户** > **客户配置** > **名称和地址选项** > **显示电话**&#x200B;并将电话号码设置为可选。
1. 使用[!DNL GraphQL API]作为登录客户下订单。
   * 设置帐单和送货地址时，请勿设置电话号码。 按照开发人员文档中的[[!DNL GraphQL] 查看教程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)中提供的说明进行操作。
1. 使用[!DNL GraphQL] [`customerOrders`查询](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/)检索订单。

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>预期的结果</u>：

用户获取订单信息。

<u>实际结果</u>：

用户收到以下错误： *&quot;message&quot;：&quot;Internal server error&quot;，*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
