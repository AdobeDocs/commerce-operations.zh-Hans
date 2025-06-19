---
title: ACSD-56790：对 [!DNL Visual Merchandiser]中的产品进行排序时，**[!UICONTROL move out of stock to bottom]**选项不起作用
description: 应用ACSD-56790补丁程序，以修复在可视化促销器中对产品进行分类时，无法正常使用“从缺货到底部”选项的Adobe Commerce问题。
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# 对[!DNL Visual Merchandiser]中的产品进行排序时，ACSD-56790： **[!UICONTROL move out of stock to bottom]**&#x200B;选项不起作用

ACSD-56790修补程序修复了在对[!DNL Visual Merchandiser]中的产品进行排序时，“从库存移至底部”选项不起作用的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44时，此修补程序可用。 修补程序ID为ACSD-56790。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对[!DNL Visual Merchandiser]中的产品进行排序时，**[!UICONTROL move out of stock to bottom]**&#x200B;选项不起作用

<u>重现步骤</u>：

1. 安装Adobe Commerce。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;并创建以下属性。
1. 创建新网站： **非主网站**。
1. 在此新网站上创建&#x200B;**非主商店**。
1. 创建两个存储：

   * 在&#x200B;**主网站商店**&#x200B;中排名第一。
   * 在&#x200B;**非主存储**&#x200B;中排名第二。

1. 创建两个源：
   * 书信。
   * 数字。

1. 创建两个库存：
   * 第一个主要 — 销售渠道：主要网站 — 分配的来源：信件。
   * 第二个非主要 — 销售渠道：非主要 — 分配的来源：数字。

1. 在两个网站上创建三个简单的产品（全部在“默认”类别中，全部分配给两个源）：

   * ProductA — 数量&#x200B;*10*&#x200B;为字母，数量&#x200B;*0*&#x200B;为数字。
   * Product1 — 数量&#x200B;*0*&#x200B;为字母，数量&#x200B;*10*&#x200B;为数字。
   * ProductA1 — 数量&#x200B;*10*&#x200B;为字母，数量&#x200B;*10*&#x200B;为数字。

1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;并选择&#x200B;**[!UICONTROL Default category]**。
1. 将作用域更改为&#x200B;**第一个**。
1. 展开“类别”部分中的产品。
1. 选择排序顺序为： **[!UICONTROL move out of stock to bottom]**

<u>预期的结果</u>：

具有&#x200B;**缺货**&#x200B;产品的产品列表将移至底部。

<u>实际结果</u>：

产品加载失败。 页面重定向到管理员仪表板，并显示错误消息： `Invalid security or form key. Please refresh the page`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
