---
source-git-commit: 00b8e1bb5ee259763ddb2c52065cee2af98641e0
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# 2024年10月Adobe Commerce 2.4.7 Beta摘要

## 高亮

此版本的Adobe Commerce包括若干关键安全修复和平台改进。

### 安全性

此版本中的以下安全增强功能改进了与最新安全最佳实践的兼容性：

>[!NOTE]
>
>有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>设置</strong></td>
            <td>此版本包括以下安全设置增强功能：
              <ul>
                <li><strong>加密密钥轮替</strong>：现在可以使用新的CLI命令更改您的加密密钥。 有关详细信息，请参阅<a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Troubleshooting Encryption Key Rotation： CVE-2024-34102</a>知识库文章。<!-- AC-12589 --></li>
                <li><strong>一次性密码(OTP)设置</strong>：需要此更新才能解决2.4.7中<a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">向后不兼容的更改</a>导致的错误。<strong>[!UICONTROL OTP Window]</strong>字段的描述现在提供了设置的准确解释，默认值已从<code>1</code>更改为<code>29</code>。<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### 平台

此版本的以下平台升级确保Adobe Commerce保持稳定可靠的平台，随时准备满足现代商务环境的需求：

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>数据库</strong></td>
            <td>根据我们的<a href="/help/release/lifecycle-policy.md">支持生命周期策略</a>，Adobe Commerce现在与以下数据库技术的以下长期支持(LTS)版本兼容：
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_（2029年之前一直受支持）_</em>：以前的版本(MariaDB 10.6)将于2026年终止生命周期，因此此升级对于保持系统完整性和性能至关重要。 虽然现在仍支持MariaDB 10.6，但Adobe建议在升级到Adobe Commerce 2.4.8时升级到MariaDB 11.4。</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_（2032年之前支持）_</em>：以前的版本(MySQL 8.0)将于2026年终止生命周期，因此此升级对于维护系统完整性和性能至关重要。 MySQL 8.0仍受支持，但Adobe建议在升级到Adobe Commerce 2.4.8时升级到MySQL 8.4</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>此版本包括以下PHP增强功能：
            <ul>
              <li><strong>PHP 8.1</strong>：此版本删除了Adobe Commerce 2.4.8的PHP 8.1兼容性。在升级到Adobe Commerce 2.4.8之前，您必须升级到PHP 8.3。</li>
              <li><strong>PHP 8.2</strong>： PHP 8.2中的一个重要更改涉及将null传递到不可为空的内部函数参数的弃用。 此发行版本解决了核心平台组件中已弃用的PHP 8.1功能，并确保与PHP 8.2兼容。</li>
              <li><strong>PHPUnit 10</strong>：此版本解决了几个关键问题，增强了兼容性，并确保Adobe Commerce测试框架符合最新的行业标准。 Adobe建议所有Commerce Marketplace供应商和具有自定义设置的客户验证其单元测试和集成测试是否在PHPUnit 10（而不是9）上运行。</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>组件</strong></td>
            <td>以下第三方<a href="/help/release/packages/adobe-commerce.md">组件和依赖项</a>已更新到最新稳定版本，以增强平台稳定性和性能：
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Search</strong></td>
            <td>Adobe Commerce现在已针对OpenSearch 2.x进行了优化，不再与Elasticsearch兼容。 代码库中现在已弃用所有Elasticsearch7和8模块和类。 Adobe强烈建议转为使用OpenSearch进行内部部署和云基础架构部署，以确保持续支持和兼容性。 请参阅<a href="/help/upgrade/prepare/opensearch-migration.md">迁移到OpenSearch</a>。
              <ul>
                <li>Elasticsearch7和Elasticsearch8选项现在在管理员配置中标记为“（已弃用）”。</li>
                <li>当用户在“管理员”配置中选择“Elasticsearch”作为搜索引擎时，Commerce显示一条通知，说明“<em>”Adobe不再支持此搜索引擎选项。 我们建议改用OpenSearch作为搜索引擎。"</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### 性能

此版本包括以下性能增强：

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>索引器</strong></td>
            <td>安装新版本的Adobe Commerce或从以前的版本升级时，所有索引器的默认<a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">索引器模式</a>现在为[!UICONTROL **Update by Schedule**]。 新的默认设置可确保索引器处于建议的配置中，从而提高系统性能并减少潜在问题。</td>
        </tr>
    </tbody>
</table>

### 质量

此版本包括以下质量增强功能：

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>库存</strong></td>
           <td>现在，系统运行时没有了InventoryIndexer引入的以前隐藏的目录依赖关系，从而确保产品创建、显示模式切换、库存状态更改和其他相关功能按预期工作。 以前，这种隐藏的依赖关系会导致不一致的情况，因为不同的实体被同步，而索引器使用不同的实体。</td>
        </tr>
        <tr>
            <td><strong>订购</strong></td>
            <td>为了尽可能减少混淆，<a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">订单详细信息</a>页面中的[!UICONTROL **Submit Comment**]按钮标签已更改为[!UICONTROL **Update**]。</td>
        </tr>
    </tbody>
</table>

### GraphQL

此版本包括以下GraphQL增强功能：

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>常规增强功能</strong></td>
           <td>此版本包括以下常规的GraphQL API增强功能：
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>：已将<code>grouped_product_image</code>和<code>configurable_product_image</code>字段添加到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a>类型。</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>：已将以下新字段添加到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a>类型以支持精确的定价显示和折扣计算：
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrices</strong>：已将<code>grand_total_excluding_tax</code>字段添加到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a>类型，从而提供了明确的含税定价。</li>
              <li><!--LYNX-542--><strong>updateCartItems突变</strong>：更新了<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a>突变，以返回包含错误详细信息而非异常的成功响应。 增强了错误映射功能，提高了用户通知的清晰度。</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config查询</strong>：在<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a>查询中引入了<code>theme</code>字段。 此字段允许您指定用于呈现reCaptcha的主题名称。</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>：在<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a>中引入了<code>quantity</code>字段以提供库存级别详细信息。 根据管理员设置，它会显示可用库存或空值。</li>
               <li><!--LYNX-460--><strong>捆绑产品</strong>：更正了捆绑产品的定价显示，确保价格和货币信息准确无误。</li>
               <li><!--LYNX-547--><strong>数量</strong>：针对数量不足且不可用的通知，优化消息传送。</li>
               <li><!--LYNX-541--><strong>UnsupportedStockError类型</strong>：添加了新的<code>InsufficientStockError</code>类型以处理库存水平不足的情况。 已调整架构以支持新的错误类型，从而增强错误报告功能。</li>
               <li><!--LYNX-476--><strong>库存金额</strong>：增强了错误消息传递功能，以包含可用的库存金额。 在订单更新期间为用户提供更清晰的库存水平洞察。</li>
               <li><!--LYNX-377--><strong>请求的数量</strong>：已将<code>not_available_message</code>添加到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>。</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>客户管理</strong></td>
           <td>此版本包括以下客户管理增强功能：
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken突变</strong>：改进了<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a>突变中的错误处理，以便为未确认的电子邮件提供特定消息。 支持更好的用户指导和错误解决。</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail突变</strong>：为重新发送电子邮件确认添加了新的<code>resendConfirmationEmail</code>突变。</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>订单管理</strong></td>
           <td>此版本包括以下用户订单管理增强功能：
             <ul>
              <li><!--LYNX-470--><strong>第一订单日期</strong>：已将新的<code>date_of_first_order</code>字段添加到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a>类型。</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>：扩展了<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a>类型以包含自定义属性，增强了订单详细信息可见性。 支持在订单确认页面上显示附加信息。</li>
              <li><!--LYNX-458--><strong>guestOrder和guestOrderByToken查询</strong>：已更新<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a>和<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a>查询以包含自定义地址属性，从而确保新帐户的完整地址信息。</li>
              <li><!--LYNX-450--><strong>CustomerOrder类型</strong>：已将<code>is_virtual</code>字段添加到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>类型，支持虚拟产品标识。 通过区分虚拟产品和物理产品来增强订单处理。</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>：添加了一个与<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a>类似的<code>OrderItemPrices</code>类型到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a>，其中包含多个新的价格字段。</li>
              <li><!--LYNX-448--><strong>合并来宾订单</strong>：改进了API功能，以便根据电子邮件匹配将来宾订单与客户帐户合并。 简化回头客户的订单管理。</li>
              <li><!-- LYNX-523: --><strong>available_actions字段</strong>：扩展了<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>类型以包含<code>available_actions</code>字段，以便更好地管理订单。 “available_actions”字段映射到枚举，其中列出了可以对订单执行的操作。</li>
              <li><!-- LYNX-524 --><strong>CustomerOrder类型</strong>：已将<code>customer_info</code>字段添加到<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>类型。 此字段需要和<code>OrderCustomerInfo</code>，后者定义有关客户名称的详细信息。</li>
              <li><!--LYNX-519--><strong>订单取消的错误代码</strong>：向<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a>类型添加了详细的错误代码。 改进了订单取消流程的错误处理和用户反馈。</li>
              <li><!--LYNX-515--><strong>使来宾用户能够创建订单退货</strong>：已调整<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a>突变以支持来宾订单退货。</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder变异</strong>：添加了新的<code>confirmCancelOrder</code>变异，以便于访客用户取消订单。</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
