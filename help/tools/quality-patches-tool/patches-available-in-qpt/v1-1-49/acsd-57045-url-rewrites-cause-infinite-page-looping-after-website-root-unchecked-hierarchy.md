---
title: ACSD-57045： URL重写导致在取消选中[!UICONTROL Website Root]中的[!UICONTROL Hierarchy]后出现无限的页面循环
description: 应用ACSD-57045修补程序以修复Adobe Commerce问题，该问题导致URL重写在[!UICONTROL Website Root]中取消选中[!UICONTROL Hierarchy]后导致无限页面循环。
feature: CMS
role: Admin, Developer
exl-id: 7beaee40-a392-4644-917e-c507e79bddcc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# ACSD-57045： URL重写导致在取消选中[!UICONTROL Website Root]中的[!UICONTROL Hierarchy]后出现无限的页面循环

ACSD-57045修补程序修复了URL重写导致在&#x200B;**[!UICONTROL Website Root]**&#x200B;取消选中&#x200B;**[!UICONTROL Hierarchy]**&#x200B;后出现无限页面循环的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-57045。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在从&#x200B;**[!UICONTROL Website Root]**&#x200B;中取消选择&#x200B;**[!UICONTROL Hierarchy]**&#x200B;后，URL重写导致无限页面循环。

<u>重现步骤</u>：

1. 创建名为&#x200B;*Test-Parent*&#x200B;的CMS页面。
1. 创建名为&#x200B;*Test-Child*&#x200B;的页面，在&#x200B;**[!UICONTROL Hierarchy]**&#x200B;部分中选择&#x200B;**[!UICONTROL Website Root]** > **[!UICONTROL Parent]**&#x200B;并保存。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**。
1. 请注意，有两个新的重写：
   * 指向&#x200B;*cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;的&#x200B;*Test-Parent*&#x200B;的请求路径
   * 指向&#x200B;*cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;的&#x200B;*Test-Child*&#x200B;的请求路径
1. 访问店面并将&#x200B;*test-child*&#x200B;添加到URL。 您应该会看到子页面。
1. 执行相同的操作，但将&#x200B;*test-parent/test-child/*&#x200B;添加到URL中并查看同一页面。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**&#x200B;并选择&#x200B;**[!UICONTROL Add URL Rewrite]**。 选择以下设置：
   * 类型： *自定义*
   * 请求路径： *test-parent/test-child*
   * 目标路径： *test-child*
   * 重定向类型： *永久(301)*
1. 访问&#x200B;*test-parent/test-child*&#x200B;路径，您应被重定向到&#x200B;*test-child*。
1. 编辑子页面（**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** >选取子页面并选择&#x200B;**[!UICONTROL Edit]**）。
1. 在&#x200B;**[!UICONTROL Hierarchy]**&#x200B;部分下，保持选择&#x200B;*Test-Parent*，但取消选择&#x200B;**[!UICONTROL Website Root]**&#x200B;并保存。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**，并注意缺少原始&#x200B;*test-child*&#x200B;到&#x200B;*cms/page/view/page_id*&#x200B;的重定向，此时它将由指向&#x200B;*test-child*&#x200B;到&#x200B;*test-parent/test-child*&#x200B;的路径替代。
1. 访问店面，并尝试访问&#x200B;*Test-Child*&#x200B;页面。

<u>预期的结果</u>：

已打开&#x200B;*Test-Child*&#x200B;页面。

<u>实际结果</u>：

未打开&#x200B;*Test-Child*&#x200B;页面。 浏览器尝试以无限循环打开&#x200B;*test-parent/test-child*&#x200B;页面。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
