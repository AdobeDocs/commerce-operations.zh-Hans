---
title: ACSD-51528：关于snake_case格式的不同行为
description: 应用ACSD-51528修补程序以修复Adobe Commerce问题，该问题导致在snake_case格式方面有不同的行为。
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528：关于snake_case格式的不同行为

ACSD-51528修补程序修复了snake_case格式的不同行为。 安装[!DNL Quality Patches Tool (QPT)] 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51528。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对snake_case格式的不同行为。

<u>重现步骤</u>：

1. 使用各种不同的属性名称测试`\Magento\Framework\Api\DataObjectHelper::populateWithArray`函数。
1. 名称类似&#x200B;*NewPName*&#x200B;的属性应该转换为&#x200B;*new_p_name*，而不是转换为&#x200B;*new_pname*。
1. 此外，在对象中使用&#x200B;*getNewPName*&#x200B;函数时，将返回&#x200B;*null*，因为&#x200B;*抽象模型*&#x200B;将正确地转换对&#x200B;*new_p_name*&#x200B;的调用，从而使这两个函数相互不兼容。

<u>预期的结果</u>

**[!UICONTROL populateWithArray]**&#x200B;函数应正确地将对象属性转换为snake_case，使其与&#x200B;**[!DNL AbstractModel's]** `Getters`和`Setters`兼容。

<u>实际结果</u>

使用&#x200B;**[!UICONTROL populateWithArray]**&#x200B;函数时，如果对象属性名称中的一行包含两个或多个大写字母，则会导致snake_case转换在最终数据数组中不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
