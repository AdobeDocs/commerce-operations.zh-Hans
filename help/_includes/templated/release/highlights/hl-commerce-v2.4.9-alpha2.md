---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---
# Adobe Commerce发行说明(v2.4.9-alpha2)

## v2.4.9-alpha2中的高亮显示

以下亮点适用于Adobe Commerce 2.4.9-alpha2版本。

### 框架

#### 添加对OpenSearch 3的支持

Adobe Commerce 2.4.9现在与OpenSearch 3.x完全兼容。此更新使商家从改进的性能、安全性和长期支持中获益，同时保持与OpenSearch 2.x的向后兼容性。

_AC-11846_

#### 将Nginx版本从1.26更新到1.28

在所有当前受支持的Adobe Commerce版本的开发和测试环境中使用的Nginx版本已从1.26更新到1.28，这与最新发布的稳定Nginx版本保持一致。
PR级别测试现在针对Nginx 1.28运行，以确认所有Adobe Commerce版本的完全兼容性和支持。

_AC-14104_

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

#### 从TinyMCE迁移到Hugerte.org

由于对TinyMCE 5和6的支持终止以及与TinyMCE 7的许可不兼容，Adobe Commerce WYSIWYG编辑器的当前实现从TinyMCE迁移到开源GreatRTE编辑器(https://hugerte.org/)。
此迁移确保Adobe Commerce保持对开源许可的合规性，避免已知的TinyMCE 6漏洞，并为商家和开发人员提供现代且受支持的编辑体验。

_AC-14568_

#### 添加对2.4.9-alpha2的完整Valkey 8.x支持

Adobe Commerce 2.4.9具有对Valkey的完整CLI命令支持，镜像当前存在的Redis功能。 已更新管理员和云配置，无缝设置Valkey。
此更新通过支持Valkey 8.x确保Adobe Commerce保持经得起未来考验和性能，并在其生命周期即将结束之际为商家和开发人员提供替代Redis的可靠选择。

_AC-14604_

### 其他

#### 更新用于CNS构建和测试的AWS Valkey 8.x服务

更新用于CNS内部版本的AWS Valkey 8.x服务

_AC-14470_

#### 2.4.9-alpha2 - 8月核心质量改进

_AC-14700_

### 安全性

#### 2.4.9-alpha2的安全改进

_AC-14610_

### 配送

#### 将USPS集成从过期的Web工具API迁移到新的RESTful USPS API

为了遵守USPS宣布于2026年1月25日停用旧版Web Tools API，已将Adobe Commerce USPS集成迁移到新的RESTful USPS API。
关键增强功能：
- Dual API支持：管理员用户现在可以通过配置设置在旧版Web Tools API和新RESTful USPS API之间进行选择。
- 身份验证升级：实施OAuth 2.0以安全API访问。
- 改进的数据格式：从XML转换为JSON，以实现更清晰、更有效的通信。
- 新管理字段：
网关REST URL（基于模式：开发或实时）
客户端ID和密码
帐户类型、帐号
CRID、MID、邮件程序标识代码
用于国际装运的AES/ITN
特定于REST的允许配送方式
此迁移可确保Adobe Commerce始终符合USPS标准，提高系统可靠性，并对商家的航运集成提供未来保障。

_AC-13257_
