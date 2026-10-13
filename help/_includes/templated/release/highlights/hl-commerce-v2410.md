---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%
---
# Adobe Commerce功能亮点(v2.4.10)

## v2.4.10-alpha1中的高亮显示

以下亮点适用于Adobe Commerce 2.4.10-alpha1版本。

### Braintree

#### 法斯特兰

通过PayPal添加Fastlane支持，可提供更快、更安全的访客结账体验。
客户可以选择保存其付款和运送详细信息，以便将来更快地进行购买。
回访的Fastlane客户可以使用一次性代码进行身份验证并检索其保存的信息。
客户还可以在结账期间添加或更改其保存的卡片和送货地址。
还支持Fastlane样式和配置选项。

_包–3521_

#### Braintree Insights

引入了Braintree Insights，以便在Magento Admin中为商家提供集中化的支付绩效报表。
提供交易、结算、拒绝、网关拒绝和支付方式数据的可见性。
支持按网站、日期范围以及每日、每周或每月间隔进行过滤。
允许商家导入最多13个月的历史交易数据以供报告。
包括数据保留和自动清理，可维护长达3年的交易数据。

_BUNDLE-3522_

#### Swish — 本地支付方式

在Braintree Magento扩展中引入Swish作为新的瑞典本地支付方法。
当满足所需的瑞典商家、国家/地区、货币和支付配置时，即可使用Swish。
具有瑞典送货地址或账单地址的客户可以在结账期间使用Swish完成支付。
添加了对具有相应签出响应的成功、已取消和失败的Swish付款流的支持。
仅当满足所有必需的配置条件时，才会显示Swish。

_BUNDLE-3523_

#### 已将版本升级到v4.9.0

已将Braintree模块从v4.8.0升级到v4.9.0。
此升级包括最新的Braintree模块更改和改进。
已验证Braintree结账和支付处理在升级后是否继续按预期工作。
现有客户结账和订单创建流程在升级后的模块中仍然可用。
进行了基本回归测试，以确保升级不会引入任何问题

_包–3530_

### 框架

#### [2.4.10-alpha1]平台组件升级

Adobe Commerce 2.4.10-alpha1包含一系列平台依赖关系升级、兼容性改进、前端库更新和稳定性修复。 此版本中包含以下已完成的更改：

- Predis：将`predis/predis`从2.x升级到3.x，改进了与Redis和Valkey环境的兼容性，并使Redis客户端与最新支持的依赖项版本保持一致。
- Magento Composer安装程序：修复了`magento-composer-installer`可能在不完成安装过程的情况下静默离开的问题，提高了基于Composer的安装的可靠性。
- 挖空.js：将挖空.js从3.5.1升级到3.5.3，以及所需的验证和兼容性更新。
- Chart.js：将Chart.js从4.5.0升级到4.5.1，包括必要的验证和兼容性更新。
- Less.js：将Less.js从4.2.2升级到4.6.4，并带有相关的验证和兼容性更新。
- Uppy：将从5.0.0升级到5.2.0，包括必需的验证和兼容性更改。
- jQuery UI：已将jQuery UI从1.14.1升级到1.14.2，并随附相关的验证和兼容性更新。
- PHP 8.5兼容性：解决了与`chr()`相关的PHP 8.5弃用问题，确保为函数提供有效的字节值，并改进了与PHP 8.5的兼容性。
- 目录搜索：修复了在处理期间`catalogsearch_fulltext`重新索引可能会停止的问题，从而提高目录搜索索引的可靠性。
- js-cookie：将js-cookie从3.0.5升级到3.0.7或适用的受支持版本，从而满足依赖性和兼容性要求。

_AC-17061_

#### 确保B2B 1.5.3-p1/1.5.4-alpha1与2.4.10-alpha1、2.4.9-p1、2.4.8-p6、2.4.7-p11和2.4.6-p16的兼容性

B2B 1.5.4-alpha1与以下Adobe Commerce发行行兼容：2.4.9、2.4.8、2.4.7和2.4.6。

_AC-17100_

#### 升级NPM依赖项并使其现代化

将以下npm依赖项更新到其最新的安全版本，以解决已知的安全漏洞：

- 下划线
- imagemin-svgo
- glob
- serve-static
- grunt
- 更少
- uglify-js
- 已标记
- clean-css
- 最小值
- trim-newlines
- terser
- css-select
- n检查
- semver-regex
- http-cache-semantics
- js-yaml
- package-json

这些依赖性更新减少了所识别的安全漏洞，同时保持了现有应用程序功能。

_AC-17372_

#### 升级NPM依赖项： underscore.js (1.13.7 → 1.13.8)

将underscore.js从1.13.7更新到1.13.8，以包含最新的上游修复和稳定性改进。

_AC-17486 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升级NPM依赖项：imagemin-svgo (9.0.0 → 12.0.0)

将imagemin-svgo从9.0.0更新到12.0.0，以包含最新的上游修复、安全更新和SVG优化改进。

_AC-17657 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升级NPM依赖项：eslint-formatter-junit (8.40.0 → 9.0.1)

将eslint-formatter-junit从8.40.0更新到9.0.1，以包含针对ESLint报表的最新上游修复和兼容性改进。

_AC-17659 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升级NPM依赖项：glob (11.0.0 → 13.0.0)

将glob从11.0.0更新到13.0.0 ，以包含最新的上游修复、性能改进和兼容性增强。

_AC-17660 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升级NPM依赖项：grunt-eslint (25.0.0 → 26.0.0)

将grunt-eslint从25.0.0更新到26.0.0，以包含最新的上游修复和兼容性改进。

_AC-17661 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升级NPM依赖项：serve-static (1.16.2 → 2.2.1)

已将服务静态从1.16.2更新为2.2.1 ，以包含最新的上游修复、安全更新和兼容性改进。

_AC-17662 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升级最新NPM依赖项，以满足Grunt和Less要求

将Grunt和Less更新到最新支持的版本，从而提高前端内部版本的稳定性和兼容性。

_AC-17663 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 将NPM覆盖依赖项升级到最新支持的版本

将多个NPM覆盖依赖项更新到最新支持的版本，从而提高安全性、构建稳定性和兼容性。

_AC-17664 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c69ec9c5)_

#### [B2B]采购订单未使用ActiveMQ自动转换为销售订单

修复了在使用ActiveMQ并通过cron (bin/magento cron:run)运行消费者时，通过启用了自动审批的店面投放的采购订单未自动转换为销售订单的问题。 以前，消息会添加到ActiveMQ队列，但除非通过CLI手动启动使用者，否则不会处理消息。 通过此修复，消费者现在可在cron运行后按预期处理消息，从而确保使用ActiveMQ的B2B商家实现无缝订单转换。

_AC-17679_

#### Symfony L2缓存优化和旧版缓存向后兼容性

Adobe Commerce 2.4.10现在提供优化的Symfony二级缓存支持，同时保留现有的基于Zend的缓存实施作为默认值。

希望使用Symfony缓存的商家必须明确启用它并更新特定于Symfony L1/L2实施的必需缓存配置。 继续使用基于Zend的缓存的现有商家无需进行任何配置更改。

这种双缓存方法使商家可以灵活地根据自己的需求采用Symfony缓存，同时确保与现有缓存配置和部署向后兼容。

_AC-17865_

### 其他

#### 国家次区域（州和省）的行政管理

商家现在可以直接从管理界面管理国家/地区子区域（例如州和省）。 这项新功能允许商家：

- 查看、添加、编辑、停用或删除任何国家/地区的区域。
- 在结账、客户地址表单以及管理订单创建期间，立即将新区域作为下拉选项提供，无需更改代码。
- 编辑区域显示名称（包括本地化的名称）和ISO代码。
- 取消激活由现有订单、地址或税则引用的区域（确保历史数据保持准确），同时防止硬删除此类区域。
- 所有预定义区域保持不变，现在可以在新界面中查看和管理。

此功能完全向后兼容，可确保面向客户的行为和API地址行为保持一致。

_AC-16192_

#### 将predis/predis从2.x升级到3.x

Redis客户端库predis/predis已从版本2.x升级到3.x。 此主要版本升级与最新的依赖关系标准保持一致，提高了兼容性，并确保了长期可维护性。

_AC-17101 - [GitHub代码贡献](https://github.com/magento/magento2/commit/de7188da)_

#### 将knockout.js从版本3.5.1升级到3.5.3

已将knockout.js库从版本3.5.1升级到3.5.3。 此更新针对所有在店面和管理员中使用挖空绑定的用户界面组件进行了上游错误修复和稳定性改进。

_AC-17366 - [GitHub代码贡献](https://github.com/magento/magento2/commit/de7188da)_

#### 将清漆升级到2.4.10-alpha1版本9

Adobe Commerce 2.4.10与Varnish版本9.0兼容。

_AC-17972_
