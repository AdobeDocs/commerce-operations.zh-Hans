---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Adobe Commerce功能亮点(v2.4.9)

## v2.4.9中的亮点

以下亮点适用于Adobe Commerce 2.4.9版本。

### REST API更改

#### 商店视图级别的REST API产品库继承控制

当有效负载中省略`media_gallery_entries`或将其设置为`NULL`时，通过存储范围中的REST API更新产品不再导致产品图像和视频继承全局范围的更改。 现在，还可以通过将相应的字段设置为`NULL`来通过REST API恢复产品图像和视频的范围继承。

在商店视图级别通过REST API更新产品时：

- 现在省略`media_gallery_entries`或将其设置为NULL将保留来自默认/全局库的继承。
- 要恢复特定库属性（如`label`、`position`、`disabled`、`video_title`、`video_description`）的继承，请在`media_gallery_entries`数组中将这些字段设置为NULL。

此更改确保存储视图可以轻松维护或恢复默认库值，从而减少混淆并使库管理更加一致。

_ACP2E-4358 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

### GraphQL API更改

#### `clearCart`GraphQL突变现已在Magento Open Source中可用

[clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/) GraphQL突变现在可供所有Magento Open Source用户使用。 以前，此突变只能在Adobe Commerce中获得。

_AC-16683 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4449d914)_

#### 来自`applyGiftCardToCart` GraphQL突变的更多描述性错误

增强了`applyGiftCardToCart`突变的错误处理。 这种变异现在会针对过期或零余额礼品卡等情况返回特定的错误消息，从而改善购物者体验。 此外，后端还防止将额外的礼品卡应用到已免费的订单中。

_LYNX-787_

#### 新的`clearWishlist`GraphQL突变一次删除所有愿望清单项

添加了`clearWishlist`突变，在一次调用中从愿望清单中删除所有项目。

_LYNX-790_

#### 基于集成的身份验证的新`exchangeExternalCustomerToken`GraphQL突变

引入了新的`exchangeExternalCustomerToken` GraphQL突变，该突变通过集成令牌对用户进行身份验证，并返回客户令牌和关联的客户数据。

_LYNX-815_


#### 新的GraphQL查询返回应用的客户组、区段和购物车规则ID

新的GraphQL查询返回已应用客户组、客户区段和购物车规则的编码`uid`。

_LYNX-867_

#### 购物车清空后自动清除礼品选项

修复了在删除所有项目后，礼品选项保留在空购物车中的问题。 现在，当购物车清空时，会自动清除赠品选项，这与优惠券的现有行为相匹配。

_LYNX-786_

#### 组合来宾购物车和客户购物车时，礼品选项会一致合并

增强了购物车合并期间的礼品选项处理能力，以确保获得更一致的用户体验。 礼品选项现在遵循优先级合并逻辑，防止在访客用户登录且其购物车与现有客户购物车合并时意外覆盖。

_LYNX-788_

#### GraphQL `OrderTotal`响应中新增了`grand_total_excl_tax`字段

新字段`OrderTotal.grand_total_excl_tax`已添加到GraphQL订单响应中。 此字段提供订单的不含税总计，使直接从API访问不含税总计更容易。

优点：

- 通过GraphQL轻松检索任何订单的总计不含税。
- 简化与需要免税总额的外部系统的集成。
- 减少客户端自定义计算的需要。

_LYNX-892_

#### 历史订单显示当前缺货产品的详细信息

现在，历史订单会显示行项目的完整产品详细信息，即使产品已缺货，因此客户和商家会保留有关购买内容的完整记录。

_LYNX-913_

#### 已将reCAPTCHA验证添加到`updateCustomer`、`updateCustomerV2`和`contactUs`GraphQL突变

为相应的店面表单启用reCAPTCHA后，`updateCustomer`、`updateCustomerV2`和`contactUs`GraphQL突变现在会强制实施相同的验证，从而帮助防止通过API自动滥用。

_LYNX-941_

#### 已将reCAPTCHA验证添加到`applyCouponsToCart` GraphQL突变中

为优惠券表单启用reCAPTCHA后，`applyCouponsToCart` GraphQL突变现在会强制执行相同的验证，从而帮助防止通过API进行优惠券代码枚举。

_LYNX-942_

#### 已恢复并完全支持B2B GraphQL API `customer_id`字段

B2B GraphQL API中的`customer_id`字段已恢复，现在在公司管理查询和变动中返回正确的值。 以前，该字段已弃用并返回`null`，这限制了其在B2B集成中的用途。

_LYNX-955_

### 管理员UI

#### 目录价格规则网格的“操作”菜单

Commerce管理员中的&#x200B;**目录价格规则**&#x200B;网格现在包括&#x200B;**操作**&#x200B;菜单，允许商家一次激活、停用或删除多个规则。 这使得目录价格规则管理与可用于&#x200B;**购物车价格规则**&#x200B;的现有批量操作一致，从而显着减少了管理大型规则集所需的时间。

_AC-13916_

#### 用于内容暂存的移动设备视图预览

管理员中的暂存预览功能现在可以准确地呈现浏览器模拟的移动设备预览，以便商家能够在移动设备上查看暂存更新上线前的显示方式。

_ACP2E-3397 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

#### 新的管理员配置可在登录时控制访客和客户购物车合并行为

商家现在可以选择在访客登录且已有客户购物车时合并购物车商品的方式：

- **访客优先级** — 使用访客购物车数量。
- **客户优先级** — 使用客户购物车数量。
- **合并数量**（默认） — 对两个数量求和。

在&#x200B;**商店** > **配置** > **销售** > **结帐**&#x200B;中，根据&#x200B;**购物车合并首选项**&#x200B;配置此行为。 该设置适用于所有产品类型，允许商家在登录时完全控制访客和客户购物车的合并方式。

_LYNX-889_

### Braintree

#### 快速签出

- **Google Pay Express Pay工资单中的促销优惠**

  Google Pay快速工资单现在支持促销和优惠代码。 购物者可以直接在Google Pay表内申请、查看和删除Commerce购物车促销活动，因此快速结账客户可获得与标准结账流程相同的折扣和激励。

  _BUNDLE-3476_

- **Apple Pay Express Pay工资单中的促销优惠**

  Apple Pay快速工资单现在支持促销和优惠代码。 购物者可以直接在Apple支付表中应用优惠券，因此快速结账用户可获得与标准结账流程相同的折扣和促销活动。

  _BUNDLE-3477_

- **Apple Pay on Chrome和Firefox**

  Apple Pay现在可用于Chrome和Firefox，而不仅仅是Safari。 启用Apple Pay Express后，PDP、迷你购物车、购物车和结账页面上会提供Apple Pay按钮，客户可以使用iPhone扫描代码来完成支付。

  _BUNDLE-3478_

- **PayPal Express的服务器端回送回调**

  PayPal Express装运回调已从客户端移至服务器端。 这直接在PayPal模式中提供动态配送方法、实时成本计算和准确的购物车级别详细信息，从而提高可靠性并为未来功能（如联系模块支持、应用程序切换流程和Venmo Express）奠定基础。

  _BUNDLE-3479_

- **PayPal联系人模块（适用于美国商家Express结帐）**

  新推出的PayPal联系人模块适用于美国商家。 启用后，购买者使用PayPal Express可以在快速流程（PDP、迷你购物车、购物车、快速结帐）期间直接在PayPal模式中查看和更新与商家共享的电子邮件地址和电话号码。 然后，所选联系人详细信息将存储在Commerce订单中。

  _包–3480_

#### 支付方式

- 对Braintree付款的&#x200B;**ELO卡类型支持**

  在Braintree支付中添加了对ELO卡类型的支持。 管理员可以在信用卡配置中启用ELO，客户可以在结账时使用ELO卡付款。

  _BUNDLE-3464_

- 波兰购物者的&#x200B;**BLIK本地付款方式**

  为波兰购物者添加了BLIK作为新的本地支付方式。 这可以在现有Braintree本地支付方法(LPM)流程中实现安全、基于银行的BLIK支付，从而改善波兰客户的结账便利性和转化。

  _BUNDLE-3481_

- **按发票付款 — 德国的新的BNPL付款方式**

  已添加[!DNL Pay Upon Invoice]作为德国买家的新本地付款方式。 [!DNL Pay Upon Invoice]是一个由PayPal和Ratepay支持的“立即购买，以后付款(BNPL)”选项(“Rechnungskauf mit Ratepay”)，它允许客户先收到货物并在30天内支付发票，无需PayPal帐户。 由于这不是即时付款，因此订单最终确定是由PayPal的服务器端webhook驱动的。

  _BUNDLE-3475_

#### 卡保险存储

- **通过帐户区域存储Google Pay**

  在Braintree中启用Google Pay Vault后，客户现在可以通过帐户区域保管其Google Pay卡。 保险存储卡显示在存储的支付方式下，可用于将来在结账时购买，并可由客户删除。 这将保险存储支持范围从Cards和PayPal扩展到Google Pay。

  _BUNDLE-3459_

- **Braintree保险存储卡的实时帐户更新程序(RTAU)**

  Braintree中新增的实时帐户更新器(RTAU)功能可确保保险存储的Visa、Mastercard和Discover卡详细信息会在卡过期或被替换时自动更新。 这样可将失败的支付降至最低，使Commerce Vault保持最新，并跳过不受支持的类型（预付、Apple Pay、Google Pay），而不会出错。

  _BUNDLE-3462_

#### 管理工具

- **将Commerce订单链接到Braintree门户**

  Braintree门户链接现已添加到Commerce管理员的订单详细信息中。 单击链接可在Braintree Portal中（在新选项卡中）使用Commerce订单中的贸易商ID和交易ID打开相关交易。 这允许直接交叉引用，而无需分别登录到两个系统。

  _BUNDLE-3461_

#### 安全性和兼容性

- **3D Secure的主集成内容安全策略更新**

  内容安全策略(CSP)已更新，以支持最新的Cardinal (3-D Secure)集成要求。 这可确保浏览器的CSP允许在3-D安全流期间使用的所有基数托管的脚本、iframe和相关资源，从而防止阻止的请求以及中断的挑战或验证体验。

  _BUNDLE-3485_

- **Braintree付款扩展PHP 8.5兼容性**

  Braintree支付扩展已更新，以支持PHP 8.5运行时，同时保持与PHP 8.4的兼容性。

  _BUNDLE-3493_

### 平台和基础架构

#### SRI哈希存储重构后，在多主题和多区域设置存储上更快地加载页面

SRI哈希存储现在按区域、主题和区域设置生成单独的文件，而不是生成单个大型`sri-hashes.json`文件。 此更改可确保为每个页面仅加载相关的哈希文件，从而缩短页面加载时间，并减少具有多个主题或区域设置的存储上的内存使用量。

_AC-16113 - [GitHub代码贡献](https://github.com/magento/magento2/commit/bc83cd2c)_

#### 添加与PHPUnit 12的兼容性

Adobe Commerce编辑器依赖项已升级到`phpunit/phpunit` 12.x。 所有测试都进行了更新，以实现兼容性、增强安全性，并与最新的PHPUnit功能保持一致。 此升级使Adobe Commerce能够为未来的PHP和PHPUnit版本做好准备。

_AC-14808_

#### 添加与RabbitMQ 4.2的兼容性

RabbitMQ 4.2现在是一个受支持的消息代理。 此更新是短期兼容性路径，允许依赖AMQP协议的商家在RabbitMQ 4.1于2026年2月终止支持之前继续使用RabbitMQ，而无需立即迁移到STOMP。 对于长期部署，使用Apache ActiveMQ Artemis作为RabbitMQ的长期替代项。

_AC-16117_

#### Apache ActiveMQ Artemis是RabbitMQ的长期替代产品

Apache ActiveMQ Artemis是Adobe Commerce推荐的长期消息代理，由RabbitMQ 4.1相关的支持终止风险驱动。 Commerce版本行2.4.6到2.4.9完全支持ActiveMQ Artemis。 在Adobe Commerce Cloud上，它以AWS ActiveMQ的形式提供，用于云原生部署。 队列使用者和发布者都可以配置为使用STOMP。


现有RabbitMQ 4安装仍与希望在短期内继续使用当前消息队列服务的商家兼容 — 请参阅上面的[添加与RabbitMQ 4.2](#add-compatibility-with-rabbitmq-42)的兼容性。 规划迁移到ActiveMQ Artemis以获得长期支持。

_AC-14558_

#### 添加对Valkey 9.x的支持

Adobe Commerce 2.4.9扩展了对Valkey作为与Redis兼容的缓存后端的支持：

- **Valkey 9.x** — Adobe Commerce 2.4.9中引入的全面支持，包括与Redis完全的CLI命令对等性以及更新的“管理”和“云”配置选项，以实现无缝设置。 这项工作由Redis 7.2支持终止和许可更改推动，为商家提供了替代Redis的完全受支持的可靠替代方案。

_AC-14103、AC-14604、AC-16122_

#### 添加对OpenSearch 3.x的支持

Adobe Commerce 2.4.9与OpenSearch 3.x完全兼容，最新的次要版本现在为推荐的搜索引擎。 商家从改进的性能、安全性和长期支持中获益，同时保持与OpenSearch 2.x的向后兼容性。

_AC-11846， AC-16403_

#### 添加对MariaDB 11.8和12.x的支持

MariaDB 11.8和12.x现在支持数据库版本，使商家能够采用最新版本以提高SQL性能和长期平台稳定性。

_AC-16533_

### PHP和编辑器

#### PHP 8.5兼容性

Adobe Commerce 2.4.9现在支持PHP 8.5和PHP 8.4，允许您在最新的安全和兼容的PHP版本上运行存储区。 所有核心功能、捆绑的扩展（包括页面生成器、B2B、Braintree等）和Adobe SaaS服务都与PHP 8.5兼容。

- 完全支持PHP 8.5和8.4。
- PHP 8.3仅允许用于升级目的（不建议用于生产）。
- 确保PCI合规性并确保Adobe Commerce安装面向未来。

_AC-15615_

#### 删除了PHP 8.2支持

从Adobe Commerce 2.4.9开始，不再支持PHP 8.2。 该平台现在针对PHP 8.3及更高版本，更新了核心代码、依赖项和工具，以在PHP 8.4和8.5上干净可靠地运行。

_AC-15758_

#### 已验证编辑器2.9的兼容性

Adobe Commerce 2.4.9与Composer 2.x（包括Composer 2.9）完全兼容。 与早期版本Composer 2.x的向后兼容性得以保留，从而确保商家和开发人员使用最新版本Composer获得稳定的构建和部署体验。

_AC-14481_

### 框架

#### JWT框架安全和兼容性更新

作为持续平台安全审查的一部分，已对Web令牌JWT框架依赖关系进行评估并将其更新到最新的主要版本，从而确保未来跨Commerce集成提供基于令牌的身份验证的兼容性和强大的安全标准。 现有功能将完全保留。

_AC-13209 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2bac8114) - [GitHub代码贡献](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub代码贡献](https://github.com/magento/magento2/commit/33b81f28)_

#### Adobe Commerce功能测试框架已更新为Symfony LTS依赖项

Adobe Commerce功能测试框架(MFTF)已更新，以根据web-token/jwt-framework升级的要求使用最新的Symfony LTS依赖项，包括symfony/config。 这解决了以前的依赖关系冲突，并确保为功能测试提供了稳定且受支持的栈栈。

_AC-13244_

#### 本机PHP OAuth函数替换第三方库

第三方`carlos-mg89/oauth`库已替换为本机PHP OAuth函数，提高了安全性，减少了外部依赖关系，并增强了平台稳定性。

_AC-14075 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7b8064f7)_

#### Symfony缓存组件取代Zend_Cache

从Adobe Commerce 2.4.9开始，已弃用的Zend_Cache组件已由Symfony Cache组件替换。 此更新增强了缓存性能和可维护性，并确保与PHP 8.x和未来平台更新的长期兼容性。 现有的缓存后端和缓存管理命令仍受完全支持，不需要更改当前集成。

_AC-15823_

#### WYSIWYG编辑器从TinyMCE迁移到GegRTE

由于对TinyMCE 5和6的支持终止以及与TinyMCE 7的许可不兼容，Adobe Commerce WYSIWYG编辑器已迁移到开源[GreatRTE](https://hugerte.org/)编辑器。 此迁移确保Adobe Commerce保持对开源许可的合规性，避免已知的TinyMCE 6漏洞，并为商家和开发人员提供现代且受支持的编辑体验。

_AC-14568_

#### 本机MVC实现取代了拉米纳斯MVC

Adobe Commerce引入了一个本机MVC实现，取代了旧版Laminas MVC，以确保超出PHP 8.5的长期兼容性和稳定性。 此更改将增强性能，减少外部依赖项，并为Commerce提供更适合未来的基础。

_AC-15160_

#### 正式的Symfony 7.4 LTS支持

作为Adobe Commerce 2.4.9平台更新的一部分，所有Symfony依赖项都已更新到最新的Symfony LTS 7.4版本。 所有扩展Symfony核心类的自定义类都更新了类型声明和方法签名，使其与最新的Symfony要求保持一致，从而防止了兼容性问题，并确保顺利过渡到更新的框架组件。

_AC-15170 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c127d10b)_

#### 诱惑PHPUnit依赖关系已升级到版本3

`allure-framework/allure-phpunit`依赖关系已升级到主要版本3，该版本添加了对PHP 8.4和PHP 8.5的支持，并使基于Allure的测试报告栈栈符合现代化要求。 旧版Allure PHPUnit以前所需的本机依赖关系已删除，从而简化了设置和维护。

_AC-14548 - [GitHub代码贡献](https://github.com/magento/magento2/commit/87b8b34e)_

#### New Relic报表已更新到NerdGraph API

New Relic报表模块已更新，以支持New Relic的NerdGraph (GraphQL)更改跟踪API，同时完全保留现有的REST v2部署标记集成。 此更改提供了更丰富的部署元数据、区域端点支持（美国和EU），以及通过管理员设置的可配置性，而不中断现有设置。

_AC-15461_

#### JavaScript库更新

- **Chart.js已更新到版本4.5.0**

  已将Chart.js JavaScript图表库升级到版本4.5.0，以提高图表渲染性能、增强可视化功能并解决管理功能板和报表模块中的安全漏洞。

  _AC-14304、AC-15133 - [GitHub代码贡献](https://github.com/magento/magento2/commit/768b4442)、[GitHub代码贡献](https://github.com/magento/magento2/commit/657f983e)_

- **文件上传库更新到4.13.4**&#x200B;版

  已将Uppy文件上传库升级到版本4.13.4，以便增强文件上传功能、改善用户体验并解决跨Adobe Commerce管理界面和前端组件的文件处理中的安全漏洞。

  _AC-14307 - [GitHub代码贡献](https://github.com/magento/magento2/commit/eb491c05)_

- **jQuery验证库已升级到版本1.21.0**

  已将jQuery Validate库升级到版本1.21.0，以增强表单验证功能、改善用户体验并确保在管理员界面和前端界面中跨所有Adobe Commerce表单实现现代浏览器兼容性。

  _AC-14403 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

- **jQuery UI库已升级到版本1.14.1**

  已将jQuery UI库升级到版本1.14.1，以便增强用户界面小组件、提高可访问性，并确保所有Adobe Commerce管理和前端界面组件都具备现代浏览器兼容性。

  _AC-14417 - [GitHub代码贡献](https://github.com/magento/magento2/commit/77c589a6)_

- **Less.js CSS预处理器已升级到版本4.2.2**

  已将Less.js CSS预处理器升级到版本4.2.2，以增强CSS编译性能、改进语法支持以及实现所有Adobe Commerce前端和管理员主题的主题构建过程的现代化。

  _AC-14418 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

- **时刻时区库已升级到版本0.5.43**

  将时刻时区库(`moment-timezone-with-data.js`)升级到版本0.5.43以增强时区处理能力，使用最新的IANA时区数据库更改更新时区数据，并改进所有Adobe Commerce国际和多时区操作的日期和时间处理准确性。

  _AC-14419 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

- **Underscore.js实用程序库已升级到1.13.7**&#x200B;版

  已将Underscore.js实用程序库升级至版本1.13.7，以增强JavaScript功能编程功能、提高数据操作性能并确保所有Adobe Commerce前端和管理员界面组件中的现代浏览器兼容性。

  _AC-14420 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

### 安全性

#### 现在强制对REST和GraphQL API进行验证码验证

为创建帐户表单启用CAPTCHA（或reCAPTCHA）后，现在将通过REST和GraphQL API对创建客户帐户强制执行相同的CAPTCHA验证。

_AC-16245_

#### 改进了异步/批量请求性能

此修复了在APSB25-08安全修补程序之后引入的批量异步Web API端点中的性能下降，从而恢复预期的执行时间。

_AC-14078 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9a7352b7)_

#### 简化的双重身份验证配置

现在，管理员用户只需配置商户启用的2FA提供商之一（例如，Google Authenticator或U2F），即可访问管理员面板。 以后可以根据需要配置其他启用的提供程序。 以前，当启用了多个2FA提供商时，要求每个管理员用户在登录之前配置所有提供商，这给无权访问每个提供商的用户造成了麻烦。

_AC-8253 - [GitHub代码贡献](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

### 配送

#### 将USPS集成迁移到RESTful USPS API

为了遵循USPS宣布的旧版Web Tools API的停用，Adobe Commerce已将其USPS集成迁移到新的RESTful USPS API。

关键增强功能：

- Dual API支持：管理员用户现在可以通过配置设置在旧版Web Tools API和新RESTful USPS API之间进行选择。
- 身份验证升级：使用OAuth 2.0进行安全API访问。
- 改进的数据格式：使用JSON而不是XML实现更清洁、更有效的通信。
- 新管理字段：
   - 网关REST URL（基于模式：开发或实时）
   - 客户端ID和密码
   - 帐户类型、帐号
   - CRID、MID、邮件程序标识代码
   - 用于国际装运的AES/ITN
   - 特定于REST的允许配送方式

此迁移可确保Adobe Commerce始终符合USPS标准，提高系统可靠性，并对商家的航运集成提供未来保障。

_AC-13257_

#### 将DHL集成迁移到MyDHL RESTful API

内置DHL传送集成现在支持MyDHL RESTful API，同时保持与旧版DHL Express XML API的兼容性。 商家可以选择在管理员中使用哪个DHL API，从而受益于现代REST功能，而无需破坏现有的基于XML的设置。

_AC-13258_
