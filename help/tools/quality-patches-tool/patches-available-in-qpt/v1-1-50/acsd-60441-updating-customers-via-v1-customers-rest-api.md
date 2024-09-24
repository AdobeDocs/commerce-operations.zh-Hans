---
title: 'ACSD-60441：通过V1/customers [!DNL REST] API端点更新客户会引发错误'
description: 应用ACSD-60441修补程序以修复Adobe Commerce问题，该问题导致在使用从后端生成的集成访问令牌时通过V1/customers [!DNL REST] API更新客户会引发错误。
feature: REST, Customers
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-60441：通过`V1/customers` [!DNL REST] API端点更新客户会引发错误

ACSD-60441修补程序修复了在使用从后端生成的集成访问令牌时通过`V1/customers` [!DNL REST] API更新客户会导致错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-60441。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p8

**与Adobe Commerce版本**&#x200B;兼容

* Adobe Commerce（所有部署方法） 2.4.4-p9、2.4.5-p8、2.4.6-p6、2.4.7-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用从后端生成的集成访问令牌通过`V1/customers` [!DNL REST] API端点更新客户时，会引发错误。

<u>重现步骤</u>：

1. 从管理员创建集成。
1. 使用集成令牌将[!DNL POST]请求发送到`rest/default/V1/customers/<customer_id>`。

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>预期的结果</u>：

客户数据已更新。

<u>实际结果</u>：

您会收到以下错误：

    ``json
    {
    ``message`： &quot;关联网站中已存在具有相同电子邮件地址的客户。&quot;，
    `trace&quot;： ...
    }
    ``

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
