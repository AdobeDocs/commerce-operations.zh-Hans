---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.33
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.33中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin
exl-id: 31812668-1d24-4da6-992f-981c259e00da
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.33

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.33中提供的修补程序所修复的问题。

QPT v1.1.33包含以下修补程序：

1. **ACSD-50478**：针对数据库转储包含触发器和分隔符SQL命令的情况，修复数据库回滚命令。
1. **ACSD-50512**：修复了错误： *可下载的链接与产品无关。 请验证链接并重试。更新可下载产品暂存更新的开始日期时发生的*。
1. **ACSD-50949**：修复了与SKU筛选器一起使用时，[!UICONTROL Advanced Search]中的价格筛选器未返回正确结果的问题。
1. **ACSD-51645**：修复了在禁用扩展`Magento_OfflineShipping`的情况下保存新[!UICONTROL Cart Price Rule]时引发的错误。
1. **ACSD-50895**：修复了未配置[!DNL Google Analytics] 4 GTM时未触发[!DNL Google Analytics] 3 GTM标记的问题。
1. **ACSD-51102**：修复了在计划更新启用编录规则时，应用于大量产品的编录规则未正确编制索引的问题。
1. **ACSD-50368**：修复了在通过异步REST API或异步批量REST API创建客户时忽略客户的`group_id`的问题。
1. **ACSD-51497**：修复了客户无法按下拉列表类型的[!UICONTROL Custom Attribute]对目录页面进行排序的问题。
1. **ACSD-51408**：修复了订单项状态错误设置为[!UICONTROL Backordered]的问题。
1. **ACSD-51735**：修复了当产品库存为&#x200B;*0*&#x200B;时，订单项状态错误设置为[!UICONTROL Ordered]的问题。
1. **ACSD-51792**：修复了在启用[!DNL Google Tag Manager] 4时页面没有展示事件的问题。
1. **ACSD-51471**：修复了管理员用户无法为捆绑产品保存计划更新的问题，捆绑产品使用本身具有计划更新的简单产品。
1. **ACSD-51700**：修复了在管理员的可下载产品编辑页面上切换商店视图时发生的错误。
1. **ACSD-51120**：修复了包含通过暂存更新更新更新的GraphQL块的CMS页面未清除CMSGET缓存的问题。
1. **ACSD-51240**：修复了通过公司注册表进行注册时上传文件缺失的问题。
1. **ACSD-51907**：修复了受限管理员用户无法创建包含离线退款的贷项通知单的问题。
1. **ACSD-52148**：修复了[!UICONTROL Google V3 reCAPTCHA Admin]登录偶尔失败的问题。
1. **ACSD-51431**：修复了即使更改日志中没有新条目，索引器状态也正常工作的问题。
1. **ACSD-51892**：修复了在部署期间配置文件加载多次的性能问题。

使用左侧的菜单导航到特定的修补程序页面。
