---
title: MDVA-39605： Redis缓存TTL（过期日期）的值错误
description: MDVA-39605修补程序解决了Redis缓存TTL（过期日期）具有错误值的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-39605。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# MDVA-39605： Redis缓存TTL（过期日期）的值错误

MDVA-39605修补程序解决了Redis缓存TTL（过期日期）具有错误值的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-39605。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Redis缓存TTL（过期日期）的值错误。

<u>重现步骤</u>：

为了测试此修复，请刷新缓存并在店面中打开可配置产品。 然后打开终端（控制台）并按照以下步骤操作：

1. 运行命令： `redis-cli`。
1. 运行`KEYS "*PRICE"` （结果中应该只有一个键，例如`zc:ti:e54_PRICE`）。 复制密钥。
1. 运行`SMEMBERS`，后跟上一步中的键（例如，`SMEMBERS zc:ti:e54_PRICE`）。 从结果复制任何密钥(例如，e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421)。
1. 使用上一步中的键名称运行`KEYS "*<key>"`以获取完整的键名称（例如，`KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`）。 结果中应该只有一个键（例如，`zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`）。 如您所见，全键名称只是前缀为“`zc:k:`”的键名称。 现在复制完整密钥名称。
1. 运行`HGETALL`，后跟步骤4中的完整密钥名称以检查该值。 该值应包含相关可配置产品的关联产品的序列化数据。
1. 运行`TTL`，后跟步骤4中的完整密钥名称，以检查密钥是否过期。 结果应不同于&#x200B;**-1**&#x200B;和&#x200B;**-2**，并应约为2592000（30天）。 尽管代码中设置的过期时间为一年，但Adobe Commerce中使用的Redis库的最大硬过期限制为2592000秒。

<u>预期的结果</u>：

到期限制为2592000秒

<u>实际结果</u>：

到期限制设置为&#x200B;**-1**&#x200B;或&#x200B;**-2**。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
