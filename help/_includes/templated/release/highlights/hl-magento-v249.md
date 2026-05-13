---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Magento Open Source功能亮点(v2.4.9)

## v2.4.9中的亮点

以下亮点适用于Magento Open Source 2.4.9版本。

### API

#### 添加了在商店视图级别更新产品时在REST API中保留产品库继承的可能性

如果从有效负荷中忽略media_gallery_entries或将其设置为NULL以防止在存储范围内的产品库中进行任何更改，则通过存储范围中的REST API更新产品不再导致产品图像和视频继承全局范围内的更改。 此外，现在可以通过将相应字段设置为NULL来通过REST API恢复产品图像和视频的范围继承。

_ACP2E-4358 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### 通过帐户区域存储Google Pay

在Adobe Commerce 2.4.9中，在Braintree中启用Google Pay Vault后，客户现在可以通过帐户区域保管其Google Pay卡。 保险存储卡显示在存储的支付方式下，可用于将来在结账时购买，并可由客户删除。 这将保险存储支持范围从Cards和PayPal扩展到Google Pay。

_BUNDLE-3459_

#### 实时帐户更新程序(RTAU)

适用于Braintree的Adobe Commerce 2.4.9中的实时帐户更新器(RTAU)功能可确保当卡到期或被替换时，保险存储的Visa、万事达卡和发现卡详细信息会自动更新。 这样可将失败的支付降至最低，使Magento Vault保持最新，并跳过不受支持的类型（预付、Apple Pay、Google Pay），而不会出错。

_BUNDLE-3462_

#### 对Braintree卡支付的ELO卡类型支持

在Adobe Commerce 2.4.9中，向Braintree Payments添加了对ELO卡类型的支持。 管理员现在可以在信用卡配置中启用ELO，客户可以在结账时使用ELO卡成功下订单，从而确保通过Braintree实现无缝交易。

_BUNDLE-3464_

#### 按发票付款

对于Adobe Commerce 2.4.9（Braintree扩展），为德国买家添加了新的本地支付方法“按发票付款”。 “发票后付款”是一种由PayPal + Ratepay支持的“立即购买，以后付款(BNPL)”选项(“Rechnungskauf mit Ratepay”)，它允许客户在30天内先收到货物并支付发票，无需PayPal帐户。 由于它不是即时支付，因此定单是由PayPal的服务器端webhook驱动的。

_BUNDLE-3475_

#### 将优惠添加到Google支付快速支付表

对于Adobe Commerce 2.4.9中的Braintree扩展，Google支付快速支付表现在支持促销/优惠代码。 购物者可以直接在Magento Pay表内申请、查看和删除Google购物车促销活动，确保快速结账客户可获得与标准结账流程相同的折扣和激励。

_BUNDLE-3476_

#### 将优惠添加到Apple支付快速支付表

对于Adobe Commerce 2.4.9中的Braintree扩展，Apple支付快速支付表现在支持促销/优惠代码。 购物者可以直接在Apple支付表中应用优惠券，因此快速结账用户可获得与标准结账流程相同的折扣和促销活动。

_BUNDLE-3477_

#### 在Chrome和Firefox上使用Apple Pay付款

对于Adobe Commerce 2.4.9中的Braintree扩展，Apple Pay现在可用于Chrome和Firefox，而不仅仅是Safari。 启用Apple Pay Express后，Apple Pay按钮在支持的店面位置均可用，客户使用iPhone扫描代码即可完成支付。

_BUNDLE-3478_

#### 服务器端送货回调

对于Adobe Commerce 2.4.9中的Braintree扩展，PayPal Express装运回调已从客户端移至服务器端。 这直接在PayPal模式中提供动态配送方法、实时成本计算和准确的购物车级别详细信息，从而提高可靠性并为未来功能（如联系模块支持、应用程序切换流程和Venmo Express）奠定基础。

_BUNDLE-3479_

#### PayPal联系人模块

对于Adobe Commerce 2.4.9中的Braintree扩展，我们为美国商家引入了新的PayPal联系模块。 启用后，购买者使用PayPal Express可以在快速流程（PDP、迷你购物车、购物车、快速结帐）期间直接在PayPal模式中查看和更新与商家共享的电子邮件地址和电话号码。 然后，所选联系人详细信息将存储在Adobe Commerce订单中。

_包–3480_

#### BLIK（本地支付方式）

在Adobe Commerce 2.4.9中的Braintree扩展中，BLIK被添加为波兰购物者的一种新的本地支付方式。 这可以在现有Braintree本地支付方法(LPM)流程中实现安全、基于银行的BLIK支付，从而改善波兰客户的结账便利性和转化。

_BUNDLE-3481_

#### 基数集成更新CSP策略

对于Adobe Commerce 2.4.9中的Braintree扩展，内容安全策略(CSP)已更新，以支持最新的Cardinal (3-D Secure)集成要求。 这可确保浏览器的CSP允许在3-D安全流期间使用的所有基数托管的脚本、iframe和相关资源，从而防止阻止的请求和中断的质询/验证体验。

_BUNDLE-3485_

### 框架

#### 已将web-token/jwt-framework库升级到最新的主要版本

作为持续安全审查流程的一部分，我们评估了JWT框架的最新主要版本，以确保未来的兼容性并维护强大的安全标准。 此版本中的现有功能不会受到影响。

_AC-13209 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2bac8114) - [GitHub代码贡献](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub代码贡献](https://github.com/magento/magento2/commit/33b81f28)_

#### [第2部分] — 使用最新可用版本更新所有js库和npm依赖项

编辑器版本支持仅针对编辑器版本2.2.x。 现在，支持也扩展到了2.4.x版本。

_AC-13792 - [GitHub代码贡献](https://github.com/magento/magento2/commit/19844aa0)_

#### 将carlos-mg89/oauth替换为PHP本机函数

将第三方carlos-mg89/oauth库替换为原生PHP OAuth函数，以提高安全性、减少外部依赖并增强平台稳定性。

_AC-14075 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7b8064f7)_

#### 升级jquery/uppy并更新库的最新版本

已将Uppy文件上传库升级到版本4.13.4，以便增强文件上传功能、改善用户体验并解决跨Adobe Commerce管理界面和前端组件的文件处理中的安全漏洞。

_AC-14307 - [GitHub代码贡献](https://github.com/magento/magento2/commit/eb491c05)_

#### 将jquery-validate库升级到最新版本

已将jQuery Validate库升级到版本1.21.0，以增强表单验证功能、改善用户体验并确保在管理员界面和前端界面中跨所有Adobe Commerce表单实现现代浏览器兼容性。

_AC-14403 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 将jquery-ui库升级到最新版本

已将jQuery UI库升级到版本1.14.1，以便增强用户界面小组件、提高可访问性，并确保所有Adobe Commerce管理和前端界面组件都具备现代浏览器兼容性。

_AC-14417 - [GitHub代码贡献](https://github.com/magento/magento2/commit/77c589a6)_

#### 将less.js库升级到最新版本

已将Less.js CSS预处理器升级到版本4.2.2，以增强CSS编译性能、改进语法支持以及实现所有Adobe Commerce前端和管理员主题的主题构建过程的现代化。

_AC-14418 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 将moment-timezone-with-data.js库升级到最新版本

将时刻时区库升级到0.5.43版以增强时区处理能力，使用最新的IANA时区数据库更改更新时区数据，并改进所有Adobe Commerce国际和多时区操作的日期/时间处理准确性。

_AC-14419 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 将underscore.js库升级到最新版本

已将Underscore.js实用程序库升级至版本1.13.7，以增强JavaScript功能编程功能、提高数据操作性能并确保所有Adobe Commerce前端和管理员界面组件中的现代浏览器兼容性。

_AC-14420 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 将allure-framework/allure-phpunit版本更新为3，并删除2.4.9-alpha1中的本机依赖项

在Adobe Commerce 2.4.9中，allure-framework/allure-phpunit依赖关系已升级到主要版本3，该版本添加了对PHP 8.4、PHP 8.5的支持，并使基于Allure的测试报告栈栈现代化。 以前的Allure PHPUnit版本所需的本机依赖关系在适用的情况下已删除，从而简化了设置和维护。

_AC-14548 - [GitHub代码贡献](https://github.com/magento/magento2/commit/87b8b34e)_

#### 将chart.js依赖关系升级到最新版本

chart.js依赖项已升级到最新版本4.5.0。

_AC-15133 - [GitHub代码贡献](https://github.com/magento/magento2/commit/657f983e)_

#### 在Adobe Commerce 2.4.9中添加对Symfony 7.4 LTS和PHP 8.5的官方支持

作为Adobe Commerce 2.4.9平台更新的一部分，magento/composer包使用的所有Symfony依赖项都已更新到最新的Symfony LTS 7.4版本。 这会使Commerce的Composer工具与当前Symfony LTS系列保持一致，并删除与较旧Symfony版本相关的先前依赖关系限制。 此外，在升级到Adobe Commerce 2.4.9之前，所有扩展Symfony核心类的自定义类都已更新与最新的Symfony要求一致的类型声明和方法签名。 这样可防止出现兼容性问题，并确保顺利过渡到更新的框架组件。

_AC-15170 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### 确保clearCart GraphQL突变在Open Source中可用

在Adobe Commerce 2.4.9中，clearCart GraphQL突变现在可供所有Open Source用户使用。 以前，此突变只能在Adobe Commerce中访问，但现在它也是Open Source的标准GraphQL购物车功能的一部分。
此突变的文档已更新，以反映其在Open Source版本2.4.9中的可用性。
请参阅[clearCart GraphQL突变文档](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/)。

_AC-16683 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9]使用管理员配置合并来宾逻辑和客户购物车逻辑

引入了一个新的管理员配置选项，用于控制购物者登录时访客和客户购物车的合并方式。 此增强功能可让您灵活地定义最适合您业务需求的购物车合并行为。

_LYNX-889_

#### [AC-2.4.9]正在获取缺货产品的历史订单

现在，即使历史订单缺货，也会显示产品详细信息。

_LYNX-913_

#### [AC-2.4.9] [CE]为缺失的GraphQL突变实施ReCaptcha

ReCaptcha验证添加到updateCustomer、updateCustomerV2和contactUs突变中。

_LYNX-941_

### 其他

#### Captcha / reCAPTCHA不适用于API / GraphQL

在Adobe Commerce 2.4.9中，为创建帐户表单启用CAPTCHA（或reCAPTCHA）后，现在将通过REST和GraphQL API对创建客户帐户强制执行相同的CAPTCHA验证。

_AC-16245 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fd7f30ee)_

#### 应更新对PHP 8.5支持的Braintree分支

Braintree支付扩展已更新，以支持最新的PHP 8.5运行时，同时保持与PHP 8.4的兼容性。

_BUNDLE-3493_

#### 添加清除愿望清单操作

添加了一个新的clearWishlist变体以支持批量操作，从而允许在一次操作中将所有项目从愿望清单中删除。

_LYNX-790_

#### 引入exchangeExternalCustomerToken突变

引入了新的GraphQL变体exchangeExternalCustomerToken ，它通过集成令牌对用户进行身份验证，并返回客户令牌和相关客户数据

_LYNX-815_

#### [AC]引入返回应用的组、区段和购物车规则ID的GraphQL查询

GraphQL查询公开以检索所应用客户组、客户区段和购物车规则的编码uid。

_LYNX-867_

#### [AC-2.4.9]引入OrderTotal.grand_total_excl_tax字段

新字段OrderTotal.grand_total_excl_tax已添加到GraphQL订单响应中。 此字段提供订单的不含税总计，使直接从API访问不含税总计更容易。

优点：

- 通过GraphQL轻松检索任何订单的总计不含税。
- 简化与需要免税总额的外部系统的集成。
- 减少客户端自定义计算的需要。

_LYNX-892_

### PCI，安全性

#### 重新调整SRI存储以提高性能效率

SRI哈希存储现在按区域、主题和区域设置生成单独的文件，而不是生成单个大型sri-hashes.json。 此更改可确保只为每个页面加载相关的哈希文件，从而提高性能并减少具有多个主题或区域设置的存储上的内存使用量。

_AC-16113 - [GitHub代码贡献](https://github.com/magento/magento2/commit/bc83cd2c)_

### 安全性

#### 提高异步/批量请求性能

修复了在APSB25-08安全修补程序之后引入的批量异步Web端点中导致执行时间增加的性能降级。

_AC-14078 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9a7352b7)_

#### 每个用户只需配置一个已启用的2FA提供程序

现在，管理员用户只需配置商户启用的2FA提供商之一（例如，Google Authenticator或U2F），即可访问管理员面板。 以后可以根据需要配置其他启用的提供程序。 以前，当启用了多个2FA提供程序（例如Google Authenticator和U2F）时，要求每个管理员用户在登录之前配置所有启用的提供程序。 这给无法访问所有因素（例如U2F的硬件密钥）的用户带来了摩擦。

_AC-8253 - [GitHub代码贡献](https://github.com/magento/security-package/commit/71e7936b)_
