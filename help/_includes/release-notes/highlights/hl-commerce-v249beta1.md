---
source-git-commit: c699c3db054dbfb6d43ad18ced4d4d860e2c9db5
workflow-type: tm+mt
source-wordcount: '2565'
ht-degree: 0%

---
# Adobe Commerce功能亮点(v2.4.9-beta1)

## v2.4.9-beta1中的亮点

以下功能亮点适用于Adobe Commerce 2.4.9-beta1版本。

### API

#### 商店视图级别的REST API产品库继承控制

当有效负载中省略`media_gallery_entries`或将其设置为`NULL`时，通过存储范围中的REST API更新产品不再导致产品图像和视频继承全局范围的更改。 现在，还可以通过将相应的字段设置为`NULL`来通过REST API恢复产品图像和视频的范围继承。

_ACP2E-4358 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 管理员UI

#### 目录价格规则网格的“操作”菜单

Commerce管理员中的“目录价格规则”网格现在包括一个“操作”菜单，允许商家一次激活、停用或删除多个目录价格规则。 这使得目录价格规则管理与可用于“购物车价格规则”的现有批量操作相一致，从而显着减少了管理大型规则集所需的时间。

_AC-13916_

#### 用于内容暂存的移动设备视图预览

管理员中的暂存预览功能现在可以准确地呈现浏览器模拟的移动设备预览，从而提供暂存更新在移动设备上显示方式的可视化表示形式。

_ACP2E-3397 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### 快速签出

- **Google Pay Express Pay工资单中的促销优惠**

  Google支付快速支付表现在支持促销和优惠代码。 购物者可以直接在Commerce Pay表内申请、查看和删除Google购物车促销活动，确保快速结账客户可获得与标准结账流程相同的折扣和激励。

  _BUNDLE-3476_

- **Apple Pay Express Pay工资单中的促销优惠**

  Apple支付快速支付表现在支持促销和优惠代码。 购物者可以直接在Apple支付表中应用优惠券，因此快速结账用户可获得与标准结账流程相同的折扣和促销活动。

  _BUNDLE-3477_

- **Apple Pay on Chrome和Firefox**

  Apple Pay现在可用于Chrome和Firefox，而不仅仅是Safari。 启用Apple Pay Express后，Apple Pay按钮在支持的店面位置均可用，客户使用iPhone扫描代码即可完成支付。

  _BUNDLE-3478_

- **PayPal Express的服务器端回送回调**

  PayPal Express装运回调已从客户端移至服务器端。 这直接在PayPal模式中提供动态配送方法、实时成本计算和准确的购物车级别详细信息，从而提高可靠性并为未来功能（如联系模块支持、应用程序切换流程和Venmo Express）奠定基础。

  _BUNDLE-3479_

- **PayPal联系人模块（适用于美国商家Express结帐）**

  新推出的PayPal联系人模块适用于美国商家。 启用后，购买者使用PayPal Express可以在快速流程（PDP、迷你购物车、购物车、快速结帐）期间直接在PayPal模式中查看和更新与商家共享的电子邮件地址和电话号码。 然后，所选联系人详细信息将存储在Commerce订单中。

  _包–3480_

#### 支付方式

- 对Braintree付款的&#x200B;**ELO卡类型支持**

  为Braintree支付添加了对ELO卡类型的支持。 管理员现在可以在信用卡配置中启用ELO，客户可以在结账时使用ELO卡成功下订单，从而确保通过Braintree实现无缝交易。

  _BUNDLE-3464_

- 波兰购物者的&#x200B;**BLIK本地付款方式**

  为波兰购物者添加了BLIK作为新的本地支付方式。 这可以在现有Braintree本地支付方法(LPM)流程中实现安全、基于银行的BLIK支付，从而改善波兰客户的结账便利性和转化。

  _BUNDLE-3481_

- **按发票付款 — 德国的新的BNPL付款方式**

  为德国买家添加了新的本地付款方法“按发票付款”。 “按发票付款”是PayPal和Ratepay提供的“立即购买，以后付款(BNPL)”选项(“Rechnungskauf mit Ratepay”)，客户可在不需要PayPal帐户的情况下，首先接收货物并在30天内支付发票。 由于这不是即时付款，因此订单最终确定是由PayPal的服务器端webhook驱动的。

  _BUNDLE-3475_

#### 卡保险存储

- **通过帐户区域存储Google Pay**

  在Braintree中启用Google Pay Vault后，客户现在可以通过帐户区域保管其Google Pay卡。 保险存储卡显示在存储的支付方式下，可用于将来在结账时购买，并可由客户删除。 这将保险存储支持范围从Cards和PayPal扩展到Google Pay。

  _BUNDLE-3459_

- **Braintree保险存储卡的实时帐户更新程序(RTAU)**

  Braintree中新增的实时帐户更新器(RTAU)功能可确保保险存储的Visa、Mastercard和Discover卡详细信息会在卡过期或被替换时自动更新。 这样可将失败的支付降至最低，使Commerce Vault保持最新，并跳过不受支持的类型(预付、Apple Pay、Google Pay)，而不会出错。

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

#### OpenSearch 3.x支持

Adobe Commerce 2.4.9-beta1与OpenSearch 3.x完全兼容。此更新使商家从改进的性能、安全性和长期支持中获益，同时保持与OpenSearch 2.x的向后兼容性。

_AC-11846_

#### 完全支持Valkey 8.x

Adobe Commerce 2.4.9-beta1添加了对Valkey 8.x作为与Redis兼容的缓存后端的全面支持，包括与Redis的完整CLI命令奇偶校验。 管理员和云配置选项已更新，以实现无缝的Valkey设置。 此支持由Redis 7.2支持终止和许可更改驱动，为商家提供了跨Commerce发行系列2.4.5到2.4.9-beta1的替代Redis的可靠且完全受支持的方案。

_AC-14103， AC-14604_

#### 将Nginx版本从1.26更新到1.28

在所有当前支持的Adobe Commerce版本的开发和测试环境中使用的Nginx版本已更新为1.28，与最新的稳定Nginx版本保持一致。 PR级别测试现在针对Nginx 1.28运行，确认所有Adobe Commerce版本完全兼容并受支持。

_AC-14104_

#### Apache ActiveMQ Artemis支持取代了RabbitMQ

添加了对Apache ActiveMQ Artemis的支持，作为RabbitMQ的战略替代方案，受RabbitMQ 4相关的支持终止风险驱动。 ActiveMQ Artemis现在在Commerce版本行2.4.6到2.4.9（测试版1）中完全受支持，包括适用于云原生部署且带有AWS ActiveMQ的Adobe Commerce Cloud，并且支持队列使用者和发布者的STOMP配置。 对于希望继续使用当前消息队列服务的商家，现有的RabbitMQ 4安装仍可兼容。

_AC-14558_

### PHP和编辑器

#### PHP 8.5兼容性

从Adobe Commerce 2.4.9-beta1开始，该平台与PHP 8.5完全兼容，同时保留对PHP 8.4的支持，并允许PHP 8.3用于仅限升级的情况。 此工作可使核心代码、依赖项和工具现代化，以便商家能够在PHP 8.4支持终止之前安全地迁移到较新的PHP版本，从而维护PCI合规性和长期平台运行状况。

_AC-15615_

#### 删除了PHP 8.2支持

从Adobe Commerce 2.4.9-beta1开始，不再支持PHP 8.2。 该平台现在针对PHP 8.3及更高版本，更新了核心代码、依赖项和工具，以在PHP 8.4和8.5上干净可靠地运行。

_AC-15758_

#### 扩展的编辑器2.x版本支持

以前，编辑器版本支持限制为2.2.x。Adobe Commerce 2.4.9-beta1扩展了此支持，以包含Composer 2.4.x及更高版本，从而拓宽了开发和部署环境的兼容性。

_AC-13792 - [GitHub代码贡献](https://github.com/magento/magento2/commit/19844aa0)_

#### 已验证编辑器2.9的兼容性

Adobe Commerce 2.4.9-beta1与Composer 2.x（包括Composer 2.9）完全兼容。这种一致性可保持向后兼容性，并确保商家和开发人员在使用最新编辑器版本时获得稳定的构建和部署体验。

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

从Adobe Commerce 2.4.9-beta1开始，已弃用的Zend_Cache组件已被Symfony Cache组件所取代。 此更新增强了缓存性能和可维护性，并确保与PHP 8.x和未来平台更新的长期兼容性。 现有的缓存后端和缓存管理命令仍受完全支持，不需要更改当前集成。

_AC-15823_

#### WYSIWYG编辑器从TinyMCE迁移到GegRTE

由于对TinyMCE 5和6的支持终止以及与TinyMCE 7的许可不兼容，Adobe Commerce WYSIWYG编辑器已迁移到开源[GreatRTE](https://hugerte.org/)编辑器。 此迁移确保Adobe Commerce保持对开源许可的合规性，避免已知的TinyMCE 6漏洞，并为商家和开发人员提供现代且受支持的编辑体验。

_AC-14568_

#### 本机MVC实现取代了拉米纳斯MVC

Adobe Commerce引入了一个本机MVC实现，取代了旧版Laminas MVC，以确保超出PHP 8.5的长期兼容性和稳定性。此更改将增强性能，减少外部依赖项，并为Commerce提供更适合未来的基础。

_AC-15160_

#### 正式的Symfony 7.4 LTS支持

作为Adobe Commerce 2.4.9-beta1平台更新的一部分，所有Symfony依赖项都已更新到最新的Symfony LTS 7.4版本。 所有扩展Symfony核心类的自定义类都更新了类型声明和方法签名，使其与最新的Symfony要求保持一致，从而防止了兼容性问题，并确保顺利过渡到更新的框架组件。

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

#### 综合多站点访问控制强化

此更新提供了对Adobe Commerce管理员中的多站点访问控制列表(ACL)的全面强化，解决了多站点访问控制配置中的已知和之前未知的权限问题。 具有特定网站或商店访问权限的管理员用户无法再查看或修改属于多站点部署中其他网站或商店的数据。

_AC-11899_

#### 现在强制对REST和GraphQL API进行验证码验证

为创建帐户表单启用CAPTCHA（或reCAPTCHA）后，现在将通过REST和GraphQL API对创建客户帐户强制执行相同的CAPTCHA验证。

_AC-16245_

#### 改进了异步/批量请求性能

此修复了在APSB25-08安全修补程序之后引入的批量异步Web API端点中的性能下降，从而恢复预期的执行时间。

_AC-14078 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9a7352b7)_

#### 简化的双重身份验证配置

现在，管理员用户只需配置商户启用的2FA提供商之一(例如，Google Authenticator或U2F)，即可访问管理员面板。 以后可以根据需要配置其他启用的提供程序。 以前，当启用了多个2FA提供商时，要求每个管理员用户在登录之前配置所有已启用的提供商，这会给无权访问所有因素的用户带来摩擦。

_AC-8253 - [GitHub代码贡献](https://github.com/magento/security-package/commit/71e7936b)_

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
