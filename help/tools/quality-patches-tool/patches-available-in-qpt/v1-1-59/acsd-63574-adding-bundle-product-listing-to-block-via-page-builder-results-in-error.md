---
title: ACSD-63574：将[!UICONTROL Bundle Product]列表添加到via [!DNL Page Builder] 的块会导致错误
description: '应用ACSD-63574修补程序以修复Adobe Commerce问题，该问题导致通过&lbrace;1**向块添加带有“复选框”或“多选”选项的**[!UICONTROL Bundle Product]会导致错误。 [!DNL Page Builder] '
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: b2e6a3a61dbd3cd3b76e968ff8cdad664663fc4b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574：通过[!DNL Page Builder]将[!UICONTROL Bundle Product]列表添加到块会导致错误

ACSD-63574修补程序修复了通过[!DNL Page Builder]将带有`Checkbox`或`Multi Select`选项的&#x200B;**[!UICONTROL Bundle Product]**&#x200B;添加到块中会导致错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-63574。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.4-p10

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用[!DNL Page Builder]将&#x200B;**[!UICONTROL Bundle Product]**&#x200B;添加到块时，产品小组件预览会中断并显示错误消息&#x200B;*很抱歉，生成此内容时出错*。 当捆绑产品包含`Checkbox`或`Multi Select`选项类型，并且`indexer dimension mode`设置为`website_and_customer_group`时，具体会发生此问题。 异常日志显示以下错误：

    &grave;&grave;
    report.CRITICAL： PDOException： SQLSTATE[42S02]：未找到基表或视图： 1146表`db_name.catalog_product_index_price_cg0_ws0`在/home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php：90
    &grave;&grave;
中不存在
<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**。
1. 在左侧面板中，展开&#x200B;**[!UICONTROL Catalog]**&#x200B;并从以下选项中选择&#x200B;**[!UICONTROL Catalog]**。
1. 向下滚动到&#x200B;**[!UICONTROL Price]**&#x200B;部分并将&#x200B;**[!UICONTROL Catalog Price Scope]**&#x200B;设置为&#x200B;**[!UICONTROL Global]**。
1. 使用以下命令将`Indexer dimension mode`设置为`website_and_customer_group`：

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. 使用捆绑选项类型`Checkbox`或`Multi Select`创建&#x200B;**[!UICONTROL Bundle Product]**，并将产品分配给类别。
1. 转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**。
1. 选择所创建产品被分配到的类别，并尝试&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>：

产品已添加，且未出现错误。

<u>实际结果</u>：

当&#x200B;**[!UICONTROL Bundle Product]**&#x200B;选项类型为`Checkbox`或`Multi Select`且`indexer dimension mode`设置为`website_and_customer_group`时，无法通过[!DNL Page Builder]添加产品。 它引发错误： *很抱歉，生成此内容时出错*。


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
