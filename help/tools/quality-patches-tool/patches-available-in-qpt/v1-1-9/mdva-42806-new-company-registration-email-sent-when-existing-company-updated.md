---
title: MDVA-42806：每次更新现有公司时都会发送新的公司注册电子邮件
description: MDVA-42806修补程序解决了每次通过REST API更新现有公司时都会发送新的公司注册电子邮件的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-42806。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: REST, B2B, Communications, Companies
role: Admin
exl-id: 4fc2ee54-d88b-4940-b6ac-e25ad61e5c66
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42806：每次更新现有公司时都会发送新的公司注册电子邮件

MDVA-42806修补程序解决了每次通过REST API更新现有公司时都会发送新的公司注册电子邮件的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9时，此修补程序可用。 修补程序ID为MDVA-42806。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

每次通过REST API更新现有公司时，都会发送新的公司注册电子邮件。

<u>先决条件</u>：

已安装B2B模块。

<u>重现步骤</u>：

1. 创建公司帐户。
1. 使用`/V1&#x200B;/company&#x200B;/<company_id>`终结点。 要更新已创建的公司，请参阅我们的开发人员文档中的[更新公司](https://developer.adobe.com/commerce/webapi/rest/b2b/company-object/#update-the-company)。 以下是有效负载示例：

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>预期的结果</u>：

由于API正在更新现有公司，因此不会发送显示“新公司注册请求”的电子邮件。

<u>实际结果</u>：

每次发送API请求时，都会发送电子邮件，说明“新公司注册请求”。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
