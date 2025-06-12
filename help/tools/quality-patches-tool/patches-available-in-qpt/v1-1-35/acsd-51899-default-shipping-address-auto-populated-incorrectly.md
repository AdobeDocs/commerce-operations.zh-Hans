---
title: ACSD-51899：默认配送地址自动填充不正确
description: 应用ACSD-51899修补程序以修复Adobe Commerce问题，该问题导致默认送货地址自动填充了错误的地址。
feature: Checkout
role: Admin
exl-id: 14e48613-6af8-476c-978d-87c27a0b0d15
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-51899：默认配送地址自动填充不正确

ACSD-51899修补程序修复了默认送货地址自动填充错误地址的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.35时，此修补程序可用。 修补程序ID为ACSD-51899。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

默认送货地址自动填充了错误的地址

<u>重现步骤</u>：

1. 在配送方式下启用&#x200B;**商店代答**。
1. 创建&#x200B;*stock*&#x200B;和&#x200B;*源*。
1. 创建产品并将产品分配给源。
1. 将产品添加到购物车。
1. 单击&#x200B;**继续从迷你购物车结帐**。
1. 输入测试电子邮件地址并选择&#x200B;**在商店中领料**。
1. 单击&#x200B;**选择商店**&#x200B;按钮，然后选择要挑选的商店位置。
1. 单击&#x200B;**下一步**&#x200B;按钮。
1. 通过单击商店徽标导航到&#x200B;**主页**。
1. 打开&#x200B;**迷你购物车**。
1. 单击名为&#x200B;**查看并编辑购物车**&#x200B;的底部超链接。
1. 单击&#x200B;**继续结帐**。
1. 单击shipping页中的shipping按钮。

<u>预期的结果</u>

除&#x200B;*国家/地区、地区和邮政编码*&#x200B;外，送货地址字段保持为空。

<u>实际结果</u>

刷新页面后，默认送货地址将自动填充&#x200B;*店内取货*&#x200B;地址。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
