---
title: 概述：[!DNL Quality Patches Tool] (QPT) v1.1.86
description: 此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.86中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 95a2c8dc890366c96b6a8129e8ee25dd1b319190
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%
---
# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.86

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.86中提供的修补程序所修复的问题。

QPT v1.1.86包含以下修补程序：

1. **ACP2E-3094**：修复了查看或编辑具有许多权限的类别的&#x200B;**[!UICONTROL Category Permissions]**&#x200B;时可能导致浏览器无响应的问题。
1. **ACP2E-5046**：修复了在管理员中创建订单时刷新页面多次添加同一SKU的问题。
1. **ACP2E-5050**：修复了在管理员中查看或保存RMA时未在&#x200B;**[!UICONTROL Action Logs]**&#x200B;报表中显示RMA编号的问题。
1. **ACP2E-5057**：修复了当&#x200B;**[!UICONTROL Catalog Price Scope]**&#x200B;设置为&#x200B;**[!UICONTROL Website]**&#x200B;时，捆绑产品的[!DNL GraphQL]查询返回全局捆绑选项价格而不是网站特定价格的问题。
1. **ACP2E-5061**：修复了类别促销规则无法将`AND`条件与匹配多个值中任意值的条件结合的问题。
1. **ACP2E-5071**：修复了在购物者的购物车已包含全部可用量时，产品页面上不始终显示库存不可用消息的问题。
1. **ACP2E-5094**：修复了在设置`MAGENTO_DC_*`环境变量时页面加载明显变慢的问题。
1. **ACP2E-5118**：修复了禁用&#x200B;**[!UICONTROL Translations]**&#x200B;缓存时[!DNL Page Builder]预览未呈现的问题。
1. **ACP2E-5134**：修复了从公司的[!UICONTROL Shared Catalog]中删除捆绑包的组件产品后，该捆绑包产品会留在购物车中，从而导致购物车和结帐期间出现错误的问题。
1. **ACP2E-5146**：修复了当其他网站上的客户与管理员用户具有相同的ID时，仅限特定网站的管理员用户无法删除客户的问题。
1. **ACP2E-5176**：修复了通过[!DNL Google Tag Manager]发送给[!DNL Google Analytics 4]的电子商务事件使用[!DNL Universal Analytics]格式并忽略多个签出事件的问题。
1. **ACP2E-5185**：修复了在类别树中移动类别时显示错误`There was a category move error`的问题，或者当存储有多个URL重写时，需要几分钟才能完成移动的问题。
1. **ACP2E-4191**：修复了禁用&#x200B;**[!UICONTROL EAV types and attributes]**&#x200B;缓存时，某些REST API请求进入无限循环的问题。
1. **ACP2E-4973**：修复了从&#x200B;**[!UICONTROL In-Store Delivery]**&#x200B;切换到其他传递方法时无法从购物车中清除关联商店地址的问题。
1. **ACP2E-5221**：修复了在多个商店和客户组的安装中启用&#x200B;**[!UICONTROL Quick Order]**&#x200B;时，**[!UICONTROL Catalog Product Permissions]**&#x200B;索引器的时间显着较长的问题。
1. **ACP2E-5245**：修复了在首次订购时使用相同地址进行配送和计费的新注册客户在下次结帐期间看到该地址被列出两次的问题。
1. **ACP2E-5248**：修复了以下问题：在[!DNL PHP] 8.5上打开&#x200B;**[!UICONTROL Add Product]**&#x200B;页面时，没有&#x200B;**[!UICONTROL Edit Product Status]**&#x200B;权限的Admin用户会看到`null as array offset`弃用错误。
1. **ACP2E-5254**：修复了在清除缓存之前，当客户打开申购单列表时，添加到申购单中的产品未显示的问题。
1. **ACP2E-5268**：修复了将&#x200B;**[!UICONTROL Enable Frontend Resize]**&#x200B;设置为&#x200B;**[!UICONTROL No]**&#x200B;时创建可配置产品失败的问题。
1. **ACP2E-3752**：修复了在创建多个产品导入操作时，产品导入处理引发错误`Undefined array key "apply_to"`的问题。
1. **ACP2E-5280**：修复了在启用&#x200B;**[!UICONTROL Category Permissions]**&#x200B;的情况下客户登录时遇到错误的问题。
1. **ACP2E-5295**：修复了在同一进程中的&#x200B;**[!UICONTROL Inventory]**&#x200B;索引器之后运行时，并行产品价格重新索引失败并出现错误`Fail in child process`的问题。
1. **ACP2E-5298**：修复了对购物车价格规则具有仅查看访问权限的管理员用户可以生成或删除优惠券代码的问题。
1. **ACP2E-5333**：修复了刷新客户区段的问题，该客户区段具有使用&#x200B;**[!UICONTROL is not]**&#x200B;运算符的&#x200B;**[!UICONTROL Total Number of Orders]**&#x200B;条件，并且有一个或多个值的值失败，出现错误`Unknown operator specified`。
1. **ACP2E-5425**：修复了客户收到同一订单的重复订单确认电子邮件的问题。

使用左侧的菜单导航到特定的修补程序页面。
