---
title: MDVA-43232：按特殊价格到顶部（或底部）对可视化促销器中的产品进行排序会导致错误
description: MDVA-43232修补程序修复了在保存类别时，按特价到顶部（或底部）对可视化促销器中的产品进行排序而导致错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43232。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232：按特殊价格到顶部（或底部）对可视化促销器中的产品进行排序会导致错误

MDVA-43232修补程序修复了在保存类别时，按特价到顶部（或底部）对可视化促销器中的产品进行排序而导致错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43232。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在可视化促销器中按“特殊价格”到“顶部”（或“底部”）对产品进行排序时，会导致在保存类别时出错。

<u>重现步骤</u>：

1. 确保有两个网站。
1. 导航到&#x200B;**商店** > **配置** > **目录** > **价格**，并设置目录价格范围=网站。
1. 再次导航到&#x200B;**商店** > **配置** > **目录** > **可视促销器** > **类别规则的可见属性** >并添加特殊价格。
1. 创建一个简单的产品，并将这些产品分配给两个网站。
1. 向产品的默认范围添加特殊价格。
1. 切换到其他商店的范围并覆盖该产品的“价格”和“特殊价格”。
1. 执行`catalog_product_price`重新索引。
1. 转到&#x200B;**目录** > **类别**&#x200B;并创建新类别。
1. 添加类别规则以筛选具有特殊价格的产品。
1. 保存类别。
1. 在“类别中的产品”部分下，将排序顺序=特殊价格设置为顶部（或底部）。
1. 再次保存类别。

<u>预期的结果</u>：

类别保存时没有出现错误。

<u>实际结果</u>：

引发异常：

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
