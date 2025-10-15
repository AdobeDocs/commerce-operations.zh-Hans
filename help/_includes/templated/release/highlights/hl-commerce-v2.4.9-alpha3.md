---
source-git-commit: dbb758dd76fd9ea2f2e2e64fb87ea03d1c426263
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---
# Adobe Commerce发行说明(v2.4.9-alpha3)

## v2.4.9-alpha3中的高亮显示

以下亮点适用于Adobe Commerce 2.4.9-alpha3版本。

### Braintree

#### 通过帐户区域存储Google Pay

在Magento 2.4.9-alpha3中，在Braintree中启用Google Pay Vault后，客户现在可以通过帐户区域保管其Google Pay卡。 保险存储卡显示在存储的支付方式下，可用于将来在结账时购买，并可由客户删除。 这将保险存储支持范围从Cards和PayPal扩展到Google Pay。

_BUNDLE-3459_

#### 将Magento订单链接到Braintree Portal订单

在Magento 2.4.9-alpha3中，Braintree Portal链接现已添加到Magento管理中的订单详细信息中。 单击链接可在Braintree Portal中（在新选项卡中）使用Magento订单中的贸易商ID和交易ID打开相关交易。 这允许直接交叉引用，而无需分别登录到两个系统。

_BUNDLE-3461_

#### 实时帐户更新程序(RTAU)

适用于Braintree的Magento 2.4.9-alpha3中的实时帐户更新器(RTAU)功能可确保当卡到期或被替换时，保险存储的Visa、万事达卡和发现卡详细信息会自动更新。 这样可将失败的支付降至最低，使Magento Vault保持最新，并跳过不受支持的类型(预付、Apple Pay、Google Pay)，而不会出错。

_BUNDLE-3462_

#### 对Braintree卡支付的ELO卡类型支持

在Magento 2.4.9-alpha3中，Braintree支付中添加了对ELO卡类型的支持。 管理员现在可以在信用卡配置中启用ELO，客户可以在结账时使用ELO卡成功下订单，从而确保通过Braintree实现无缝交易。

_BUNDLE-3464_

### 框架

#### 从RabbitMQ迁移到Apache ActiveMQ

_AC-14558_

#### 将chart.js依赖关系升级到最新版本

chart.js依赖项已升级到最新版本4.5.0

_AC-15133 - [GitHub代码贡献](https://github.com/magento/magento2/commit/657f983e)_

#### 从层级MVC迁移

Adobe Commerce引入了一个本机MVC实现，取代了旧版Laminas MVC，以确保超出PHP 8.5的长期兼容性和稳定性。此更改将增强性能，减少外部依赖项，并为Commerce提供更适合未来的基础

_AC-15160_

### 安全性

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-94](https://helpx.adobe.com/cn/security/products/magento/apsb25-94.html)。

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}
