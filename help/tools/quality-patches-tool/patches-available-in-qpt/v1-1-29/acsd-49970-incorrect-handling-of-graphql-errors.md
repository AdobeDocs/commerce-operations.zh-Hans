---
title: ACSD-49970：GraphQL错误的处理不正确
description: Adobe Commerce应用ACSD-49970修补程序以修复以下问题：打开[!UICONTROL New Relic Reporting]时，GraphQL错误的处理不正确。
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970：GraphQL错误的处理不正确

ACSD-49970修补程序修复了在打开&#x200B;*[!UICONTROL New Relic Reporting]*&#x200B;时无法正确处理GraphQL错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49970。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无论`GraphQLOperationNames`是否包含此密钥，`logDataHelper`密钥都未正确处理。

<u>重现步骤</u>：

1. 运行`bin/magento deploy:mode:set developer`。
1. 登录到管理员。
1. 从&#x200B;**[!UICONTROL New Relic Integration]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**&#x200B;启用&#x200B;**[!UICONTROL New Relic Reporting]**
（注意：即使显示错误消息，称[!DNL New Relic]扩展不可用，配置也会保存）。
1. 从&#x200B;*客户端或任何其他客户端或通过cURL运行此* GraphQL`http://yourMagentoDomain/graphql`突变到&#x200B;*[!DNL Altair]*。

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   （注意：将&#x200B;**[!UICONTROL Header]**&#x200B;设置为[!UICONTROL Content-Currency:CA]，然后再运行它）。

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>预期的结果</u>：

日志中没有&#x200B;*500异常*，正在正确处理`GraphQLOperationNames`密钥。

<u>实际结果</u>：

日志中存在&#x200B;*500异常*，未正确处理`GraphQLOperationNames`密钥。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
