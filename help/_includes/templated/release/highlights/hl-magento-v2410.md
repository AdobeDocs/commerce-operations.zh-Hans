---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%
---
# Magento Open Source功能亮点(v2.4.10)

## v2.4.10-alpha1中的高亮显示

以下亮点适用于Magento Open Source 2.4.10-alpha1版本。

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

### 其他

#### 将predis/predis从2.x升级到3.x

Redis客户端库predis/predis已从版本2.x升级到3.x。 此主要版本升级与最新的依赖关系标准保持一致，提高了兼容性，并确保了长期可维护性。

_AC-17101 - [GitHub代码贡献](https://github.com/magento/magento2/commit/de7188da)_

#### 将knockout.js从版本3.5.1升级到3.5.3

已将knockout.js库从版本3.5.1升级到3.5.3。 此更新针对所有在店面和管理员中使用挖空绑定的用户界面组件进行了上游错误修复和稳定性改进。

_AC-17366 - [GitHub代码贡献](https://github.com/magento/magento2/commit/de7188da)_
