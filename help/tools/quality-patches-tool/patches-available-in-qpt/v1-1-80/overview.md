---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.80
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.80中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 08101f36665d77f807386f261d39dee1e379a8b1
workflow-type: tm+mt
source-wordcount: 465
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.80

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.80中提供的修补程序所修复的问题。

QPT v1.1.80包含以下修补程序：

1. **ACP2E-4239**：修复了由于所选日期、存储的UTC值和配置的存储区时区之间的时区差异，使用日期属性的管理网格筛选器返回错误结果的问题。
1. **ACP2E-4472**：修复了在&#x200B;**[!UICONTROL Login as Customer]**&#x200B;流程中创建null引号的问题。
1. **ACP2E-4481**：修复了在取消订单后无法正确重新计算捆绑产品可销售性的问题。
1. **ACP2E-4488**：修复了属性集大的产品在[!UICONTROL Admin]中保存或编辑产品速度缓慢的问题。
1. **ACP2E-4493**：修复了在启用异步索引时，销售订单存档网格显示错误订单状态的问题。
1. **ACP2E-4496**：修复了Analytics cron作业在执行期间导致性能下降，从而改善整体系统性能的问题。
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**：修复了URL中包含商店代码时，店面未加载占位符图像的问题。
1. **ACP2E-4552**：修复了GraphQL响应中未返回公司状态的问题。
1. **ACP2E-4610**：修复了`sales_clean_quotes` cron作业存在性能问题的问题。
1. **ACP2E-4615**：修复了在线订单退款失败并出现PayPal错误的问题，即&#x200B;*PayPal网关拒绝请求。 内部错误。*。
1. **ACP2E-4626**：修复了某些Storefront JavaScript文件被请求和执行两次，从而导致间歇性重复加载和不稳定的问题。
1. **ACP2E-4653**：修复了在通过REST API检索或更新规则时未公开&#x200B;**[!UICONTROL Category (Parent Only)]**&#x200B;和&#x200B;**[!UICONTROL Category (Children Only)]**&#x200B;的&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;条件属性范围的问题。
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**：修复了storefront产品页面上的Weight属性在&#x200B;**[!UICONTROL Additional Information]**&#x200B;或&#x200B;**[!UICONTROL More Information]**&#x200B;部分中只显示原始数值而没有配置的度量单位（lbs或kgs）的问题。
1. **ACP2E-4156**：修复了REST API中的送货地址验证不遵循[!UICONTROL Admin]中定义的属性配置的问题。
1. **ACP2E-4808**：修复了storefront产品页面上的Weight属性在&#x200B;**[!UICONTROL Additional Information]**&#x200B;或&#x200B;**[!UICONTROL More Information]**&#x200B;部分中只显示原始数值而没有配置的度量单位（lbs或kgs）的问题。
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**：修复了[!DNL REST] API中的送货地址验证不符合管理员中定义的属性配置的问题。
1. **ACP2E-4813**：修复了以下问题：在结账时无法使用USPS配送方式，并且某些产品的配送估计不正确，包括拆分为多个套件的订单。
1. **ACSD-53502**：修复了以下问题：由于递归调用New Relic监视脚本，导致&#x200B;**[!UICONTROL Add to Cart]**&#x200B;在iOS [!DNL Safari]中的店面间歇性地失败，进而导致页面重新加载。

使用左侧的菜单导航到特定的修补程序页面。
