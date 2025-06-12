---
title: MDVA-43178：无法在GraphQL中检索自定义存储区的客户令牌
description: MDVA-43178修补程序修复了无法在GraphQL中检索自定义存储区的客户令牌的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-43178。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: GraphQL
role: Admin
exl-id: 8dd9c9e7-573c-4c7a-8fd0-3b3886649af3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-43178：无法在GraphQL中检索自定义存储区的客户令牌

MDVA-43178修补程序修复了无法在GraphQL中检索自定义存储区的客户令牌的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14时，此修补程序可用。 修补程序ID为MDVA-43178。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法在GraphQL中检索自定义存储区的客户令牌。

<u>重现步骤</u>：

1. 为默认存储创建两个存储视图。
1. 创建一个新网站、一个商店和一个商店视图。 将此商店视图命名为“test3”。
1. 为新网站创建客户。
1. 生成API管理令牌：

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    {
      "username": "login",
      "password": "password"
    }
    </code>
    </pre>

1. 发送GraphQL以管理员身份检索客户令牌，使用管理员令牌进行授权，在标头中为“store”=“test3”：

   <pre>
    <customer_email>
      </pre>

<u>预期的结果</u>：

生成客户令牌。

<u>实际结果</u>：

未生成客户令牌。 商家收到&#x200B;*提供的客户电子邮件不存在*&#x200B;作为回应。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
