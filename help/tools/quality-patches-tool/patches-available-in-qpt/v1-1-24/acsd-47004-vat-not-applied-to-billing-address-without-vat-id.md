---
title: ACSD-47004：增值税未应用于没有VAT ID的帐单地址
description: 应用ACSD-47004修补程序以修复以下Adobe Commerce问题：如果帐单地址没有VAT ID，则不会对其应用VAT。
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 1%

---

# ACSD-47004：增值税未应用于没有VAT ID的帐单地址

ACSD-47004修补程序修复了在没有VAT ID的帐单地址中不应用VAT的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-47004。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果帐单地址没有VAT ID，则不应用VAT。

<u>重现步骤</u>：

1. 打开[!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]**，并将&#x200B;**[!UICONTROL Enable Automatic Assignment to Customer Group]**&#x200B;设置为&#x200B;*[!UICONTROL Yes]*。
1. 为VAT ID验证设置不同的组。 例如：

   ![VAT-ID验证](/help/assets/tools/vat-id-validations.png)

1. 注册新客户。
1. 添加新的默认地址，而不使用VAT。 例如：

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. 验证客户的组是否仍为[!UICONTROL General]。
1. 编辑此地址并添加有效的VAT编号：

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. 确保客户的组已更改为[!UICONTROL Retailer]。
1. 编辑地址并删除VAT编号：

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>预期的结果</u>：

客户组已自动更改为默认[!UICONTROL General]组。

<u>实际结果</u>：

客户组未自动更改为默认[!UICONTROL General]组。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
