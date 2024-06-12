---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7安全增强功能

到目前为止，尚未发生与这些问题相关的已确认攻击。 但是，可能会利用某些漏洞访问客户信息或接管管理员会话。 这些问题中的大多数要求攻击者首先获得对管理员的访问权限。 因此，我们提醒您采取一切必要步骤保护您的管理员，包括但不限于以下工作：

* IP 列入允许列表
* [双重身份验证](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* 使用VPN
* 使用唯一位置，而不是 `/admin`
* 良好的密码卫生

此版本的安全性改进改进了与最新安全最佳实践的兼容性。

* **更改了未生成的缓存键的行为**：

   * 块的非生成缓存键现在包含与自动生成的键的前缀不同的前缀。 (未生成缓存键是通过template指令语法或 `setCacheKey` 或 `setData` 方法。)
   * 块的非生成缓存键现在只能包含字母、数字、连字符(-)和下划线字符(_)。  <!-- AC-9831 -->

* **对自动生成优惠券代码数量的限制**. Commerce现在限制自动生成的优惠券代码数量。 默认最大值为250,000。 商家可以使用新的 **[!UICONTROL Code Quantity Limit]** 配置选项(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)，以防止使用大量优惠券使系统不堪重负。 <!-- AC-8753 -->

* **优化默认管理员URL生成流程**. 默认管理员URL的生成针对增加的随机性进行了优化，这使得生成的URL更不可预测。 <!-- AC-9028 -->

* **添加了子资源完整性(SRI)支持** 以符合PCI 4.0的要求，验证支付页面上的脚本完整性。 子资源完整性(SRI)支持为驻留在本地文件系统中的所有JavaScript资产提供完整性哈希。 默认SRI功能仅在管理员和店面区域的支付页面上实施。 但是，商家可以将默认配置扩展到其他页面。 请参阅 [子资源完整性](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) 在 _Commerce PHP开发人员指南_.<!--AC-1153-->

* **对内容安全策略(CSP)的更改** — 对Adobe Commerce内容安全策略(CSP)进行了配置更新和增强以符合PCI 4.0要求。 有关详细信息，请参阅 [内容安全策略](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 在 _Commerce PHP开发人员指南_. <!--AC-11513-->

   * Commerce管理员和店面区域的付款页面的默认CSP配置现在为 `restrict` 模式。 对于所有其他页面，默认配置为 `report-only` 模式。  在低于2.4.7的版本中，CSP配置于 `report-only` 模式。

   * 添加了一个nonce提供程序，以允许在CSP中执行内联脚本。 nonce提供程序有助于为每个请求生成唯一的nonce字符串。 随后，这些字符串将附加到CSP标头。

   * 添加了用于配置自定义URI以报告“管理员”中“创建订单”页面和“店面”中“结帐”页面的CSP违规的选项。 您可以从管理员添加配置，或通过将URI添加到 `config.xml` 文件。

     >[!NOTE]
     >
     >正在将CSP配置更新到 `restrict` 模式可能会阻止管理员和店面中付款页面上现有的内联脚本，这会导致页面加载时出现以下浏览器错误： `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. 通过更新白名单配置以允许所需的脚本修复这些错误。 请参阅 [疑难解答](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) 在 _Commerce PHP开发人员指南_.

* 新的全页缓存配置设置可帮助减轻与HTTP相关的风险 `{BASE-URL}/page_cache/block/esi` 端点。 此端点支持来自Commerce布局句柄和块结构的无限制、动态加载的内容片段。 新 **[!UICONTROL Handles params size]** 配置设置设置此端点的值 `handles` 参数，用于确定每个API允许的最大句柄数。 此属性的默认值为100。 商家可以从管理员(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**)。 请参阅 [配置Commerce应用程序以使用Varnish](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **通过REST和GraphQL API传输的支付信息的本机速率限制**. 商家现在可以 [配置速率限制](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) ，以了解通过REST和GraphQL传输的付款信息。 此新增的保护层支持对分拣攻击的防范，并可能会减少一次测试多个信用卡号码的分拣攻击的数量。 这是现有REST端点的默认行为的更改。 请参阅 [限速](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* 的默认行为 [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查询和([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端点已更改。 默认情况下，API现在始终返回 `true`. 商家可以通过设置 *[启用来宾签出登录](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* 管理员中的选项用于 `yes`，但这样做可能会将客户信息泄露给未经身份验证的用户。
