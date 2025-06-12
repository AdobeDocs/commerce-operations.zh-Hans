---
title: ACSD-54106：更正产品类别中的土耳其重音字符排序
description: 应用ACSD-54106修补程序以修复按名称对土耳其语重音字符进行类别产品排序不正确的Adobe Commerce问题。
feature: Categories, Products, Search
role: Admin
exl-id: 45c8efbb-85d0-4d25-9d7e-9c41a97e80fa
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-54106：更正产品类别中的土耳其重音字符排序

ACSD-54106修补程序修复了按名称对土耳其语重音字符进行类别产品排序不正确的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39时，此修补程序可用。 修补程序ID为ACSD-54106。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

按名称对类别中产品的排序对于土耳其重音字符不正确。

<u>重现步骤</u>：

1. 登录到管理面板。
1. 创建名为的简单产品，并将其分配给任何类别：

* 名称A
* 名称C
* 名称D
* 名称
* 名称M
* 陶姓
* 姓氏U
* 名称Y
* 名称Z

1. 导航到店面并访问包含产品的类别。
1. 将排序顺序修改为&#x200B;*[!UICONTROL By Name]*。

<u>预期的结果</u>：

产品按以下顺序正确排序：

* 名称A
* 名称C
* 名称D
* 名称
* 名称M
* 陶姓
* 姓氏U
* 名称Y
* 名称Z

<u>实际结果</u>：

产品按以下顺序错误排序：

* 名称A
* 名称D
* 名称M
* 名称Y
* 名称Z
* 名称C
* 陶姓
* 姓氏U
* 名称

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
