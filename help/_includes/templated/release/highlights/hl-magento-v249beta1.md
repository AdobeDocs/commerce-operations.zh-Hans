---
source-git-commit: 56974b4ada65c21ce1303e4b93bd8acb9fe41b28
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---
# Magento Open Source功能亮点(v2.4.9-beta1)

## v2.4.9-beta1中的亮点

以下功能亮点适用于Magento Open Source 2.4.9-beta1版本。

### API

#### 添加了在商店视图级别更新产品时在REST API中保留产品库继承的可能性

如果从有效负荷中忽略media_gallery_entries或将其设置为NULL以防止在存储范围内的产品库中进行任何更改，则通过存储范围中的REST API更新产品不再导致产品图像和视频继承全局范围内的更改。 此外，现在可以通过将相应字段设置为NULL来通过REST API恢复产品图像和视频的范围继承

_ACP2E-4358 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 框架

#### 调查web-token/jwt-framework的最新主要版本

作为持续安全审查流程的一部分，我们评估了JWT框架的最新主要版本，以确保未来的兼容性并维护强大的安全标准。 此版本中的现有功能不会受到影响。

_AC-13209 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2bac8114) - [GitHub代码贡献](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub代码贡献](https://github.com/magento/magento2/commit/33b81f28)_

#### [第2部分] — 使用最新可用版本更新所有js库和npm依赖项

编辑器版本支持仅针对编辑器版本2.2.x。 现在，支持也扩展到了2.4.x版本。

_AC-13792 - [GitHub代码贡献](https://github.com/magento/magento2/commit/19844aa0)_

#### 将carlos-mg89/oauth替换为PHP本机函数

将第三方carlos-mg89/oauth库替换为原生PHP OAuth函数，以提高安全性、减少外部依赖并增强平台稳定性。

_AC-14075 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7b8064f7)_

#### 调查最新版本的chart.js

已将Chart.js JavaScript图表库升级到最新版本4.4.8，以提高图表渲染性能、增强视觉功能并解决管理功能板和报表模块中的安全漏洞。

_AC-14304 - [GitHub代码贡献](https://github.com/magento/magento2/commit/768b4442)_

#### 调查最新版本jquery/uppy并更新

已将Uppy文件上传库升级到版本4.13.4，以便增强文件上传功能、改善用户体验并解决跨Adobe Commerce管理界面和前端组件的文件处理中的安全漏洞。

_AC-14307 - [GitHub代码贡献](https://github.com/magento/magento2/commit/eb491c05)_

#### 调查最新版本的jquery-validate

已将jQuery Validate库升级到版本1.21.0，以增强表单验证功能、改善用户体验并确保在管理员界面和前端界面中跨所有Adobe Commerce表单实现现代浏览器兼容性。

_AC-14403 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 调查最新版本的jquery-ui

已将jQuery UI库升级到版本1.14.1，以便增强用户界面小组件、提高可访问性，并确保所有Adobe Commerce管理和前端界面组件都具备现代浏览器兼容性。

_AC-14417 - [GitHub代码贡献](https://github.com/magento/magento2/commit/77c589a6)_

#### 调查最新版本less.js

已将Less.js CSS预处理器升级到版本4.2.2，以增强CSS编译性能、改进语法支持以及实现所有Adobe Commerce前端和管理员主题的主题构建过程的现代化。

_AC-14418 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 调查最新版本moment-timezone-with-data.js

将时刻时区库升级到0.5.43版以增强时区处理能力，使用最新的IANA时区数据库更改更新时区数据，并改进所有Adobe Commerce国际和多时区操作的日期/时间处理准确性。

_AC-14419 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 调查最新版本的underscore.js

已将Underscore.js实用程序库升级至版本1.13.7，以增强JavaScript功能编程功能、提高数据操作性能并确保所有Adobe Commerce前端和管理员界面组件中的现代浏览器兼容性。

_AC-14420 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98b2848a)_

#### 将allure-framework/allure-phpunit版本更新为3，并删除2.4.9-alpha1中的本机依赖项

在Adobe Commerce 2.4.9中，allure-framework/allure-phpunit依赖关系已升级到主要版本3，该版本添加了对PHP 8.4、PHP 8.5的支持，并使基于Allure的测试报告栈栈现代化。 以前的Allure PHPUnit版本所需的本机依赖关系在适用的情况下已删除，从而简化了设置和维护。

_AC-14548 - [GitHub代码贡献](https://github.com/magento/magento2/commit/87b8b34e)_

#### 将chart.js依赖关系升级到最新版本

chart.js依赖项已升级到最新版本4.5.0

_AC-15133 - [GitHub代码贡献](https://github.com/magento/magento2/commit/657f983e)_

#### 在Adobe Commerce 2.4.9中添加对Symfony 7.4 LTS和PHP 8.5的官方支持

作为Adobe Commerce 2.4.9平台更新的一部分，magento/composer包使用的所有Symfony依赖项都已更新到最新的Symfony LTS 7.4版本。 这会使Commerce的Composer工具与当前Symfony LTS系列保持一致，并删除与较旧Symfony版本相关的先前依赖关系限制。 此外，在升级到Adobe Commerce 2.4.9之前，所有扩展Symfony核心类的自定义类都已更新与最新的Symfony要求一致的类型声明和方法签名。这样可防止出现兼容性问题，并确保顺利过渡到更新的框架组件。

_AC-15170 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c127d10b)_

### 其他

#### Captcha/reCaptha不适用于API/GraphQl

在Adobe Commerce 2.4.9中，为创建帐户表单启用CAPTCHA（或reCAPTCHA）后，现在将通过REST和GraphQL API对创建客户帐户强制执行相同的CAPTCHA验证。

_AC-16245 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fd7f30ee)_

### 安全性

#### 提高异步/批量请求性能

修复了在APSB25-08安全修补程序之后引入的批量异步Web端点中导致执行时间增加的性能降级。

_AC-14078 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9a7352b7)_

#### 每个用户只需配置一个已启用的2FA提供程序

现在，管理员用户只需配置商户启用的2FA提供商之一(例如，Google Authenticator或U2F)，即可访问管理员面板。 以后可以根据需要配置其他启用的提供程序。 以前，当启用了多个2FA提供程序(例如Google Authenticator和U2F)时，要求每个管理员用户在登录之前配置所有启用的提供程序。 这给无法访问所有因素（例如U2F的硬件密钥）的用户带来了摩擦。

_AC-8253 - [GitHub代码贡献](https://github.com/magento/security-package/commit/71e7936b)_

### 暂存和预览

#### [功能请求]移动视图中的内容暂存预览

管理员面板中的暂存预览功能现在可以准确地呈现浏览器模拟的移动设备预览，从而提供暂存更新在移动设备上显示方式的可视化表示形式。

_ACP2E-3397 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_
