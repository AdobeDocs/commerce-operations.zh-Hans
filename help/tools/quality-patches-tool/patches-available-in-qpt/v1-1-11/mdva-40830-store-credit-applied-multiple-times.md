---
title: 'MDVA-40830：在订单期间多次应用商店点数'
description: MDVA-40830修补程序修复了在下单期间多次应用商店点数的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11后，即可使用此修补程序。 修补程序ID为MDVA-40830。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Orders, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-40830：在订单期间多次应用商店点数

MDVA-40830修补程序修复了在下单期间多次应用商店点数的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11时，此修补程序可用。 修补程序ID为MDVA-40830。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.3.7-p2、2.4.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

下单期间会多次应用商店积分。

<u>重现步骤</u>：

1. 创建客户并将商店贷记添加到客户帐户。
1. 将简单产品添加到购物车。
1. 设置购物车的送货地址和帐单地址。
1. 检查购物车的grand_total。
1. 使用以下GraphQL请求将商店积分应用于购物车：

<pre>
<code class="language-graphql">
mutation {
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) {
    cart {
      prices {
        grand_total {
          currency
          value
        }
      }
      applied_store_credit {
        applied_balance {
          currency
          value
        }
        current_balance {
          currency
          value
        }
      }
    }
  }
}
</code>
</pre>

<u>预期的结果</u>：

applied_store_credit的值应用准确，购物车总计情况正确反映在API响应中。

<u>实际结果</u>：

applied_store_credit的值应用两次，这会同时影响购物车和grand_total。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。