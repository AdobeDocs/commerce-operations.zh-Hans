---
title: 自托管Adobe Commerce安全概念
description: 了解自托管安全概念以及要考虑的最佳实践。 了解只读文件系统、恶意软件扫描等概念，以及托管Adobe Commerce时要考虑的许多其他主题。
landing-page-description: 了解自行托管Adobe Commerce时应考虑的一些安全概念和事项。
short-description: 了解自行托管Adobe Commerce的策略和安全概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: f76a8906-af31-4a61-be68-f5dad87161e2
feature: Install, Security
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 0%

---

# 安全概念

对于任何与电子商务项目相关的内容，安全性应始终是一个强有力的考虑因素。 如果没有强大的安全防御，可以遭受攻击的表面面积将呈指数级增长。 所提出的概念和想法提供了经证明可降低通常所利用的常见漏洞的方法。

以下概念不是按特定顺序排列的。 它们旨在提供一些想法和概念以供考虑。 其中许多是免费的，或者需要最低限度的设置和配置以及随后的监控。 在本教程之外研究这些主题，以确保您对此处介绍的概念有足够深入的了解。

## 只读文件系统

从云基础架构](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}上的[Adobe Commerce借用了只读文件系统概念。 这将完全删除不良操作者使用的一个主要区域。 许多漏洞利用更改预期位于Commerce应用程序中的文件来避免检测。 错误操作者不会创建操作，而是更改现有文件的内容以执行意外操作。 使文件系统为只读会显着减少此攻击向量。

## 使用双重身份验证和密码管理器

切勿共享密码。 每个管理员用户都应拥有自己的帐户，并具有适当的ACL。 确保从未禁用或移除两个因子标识。 如果您向第三方提供管理员访问权限，请确保密码由密码管理器生成，且不得重复使用。

## 恶意软件扫描

恶意软件扫描通常可以从尝试在Adobe Commerce中专门化的托管提供商找到。 随着新威胁的发现、分类和诊断，这个已知的恶意软件和漏洞库日益增加。 查询托管提供程序是否具有此类服务，以及它们是否可以自动运行或仅在请求时运行。 还有一些您可以订阅的服务，这些服务可以使用他们自己的已知利用漏洞库来不断检查您的商业应用程序中的利用漏洞。 其中有些只是外部的，有些可以添加到基础结构中以对所有文件夹、文件甚至数据库进行内部深层扫描。 从Sansec.io到Sucuri，当然还有MageReport，有一些提供商在这方面拥有多年的经验。 有些是免费的，有些则附有相关费用。 了解这一点并与Adobe Commerce架构师和开发运营团队进行深入细致的对话将确保您找到正确的解决方案。

## 适用于Commerce的站点范围分析工具

[全站点分析工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"}是一个主动式自助服务工具和中央存储库，其中包含详细的系统分析和建议，以确保Adobe Commerce安装的安全性和可操作性。 它提供全天候的实时性能监控、报告和建议，以发现潜在问题并更好地了解站点运行状况、安全性和应用程序配置。 它有助于缩短解决时间并提高站点稳定性和性能。

## 启用并验证管理员操作日志记录设置

在登录Adobe Commerce管理员并导航到“存储” > “配置” > “高级” > “管理员” > “管理员操作日志记录”后，即可找到该标记。 这将提供被监视和记录的事件列表。 如果在受攻击的站点上执行取证分析，并且怀疑这些站点已获得Commerce管理员的访问权限，则此功能非常有用。 此日志记录和报告有助于查看错误操作者执行了哪些事件。 如果禁用了任何管理员操作日志记录，则表明执行某些操作时，有人可能出于保护目的而禁用了这些日志记录，请删除日志记录。

## 用于ssh访问的堡垒服务器

这很难解释“安全概念”教程中的大多数主题。 其基本思想是提供一个服务器，充当访问ssh的中间人。 这样，您的生产服务器就永远不允许外部ssh连接。 您可以创建此堡垒服务器并使用本地IP掩码，以确保只允许指定的服务器通过SSH连接到这些服务器。

## 查看ACL角色和权限

Adobe Commerce的每位管理员用户都分配有一个ACL角色。 应创建此角色，以仅提供必须执行作业的功能。 应经常评估ACL角色，以确保它们不会提供超出必要的权限。 如果需要，请创建多个ACL角色并赋予其职责。 如果由于某种原因将访问权限授予第三方，则应尽快停用这些权限。 询问他们确实需要访问多长时间，并在创建管理员用户时设置自动过期日期。

## 经常审核管理员用户和SSH用户访问

要检测不需要或未经授权的管理员用户创建，应经常审核管理员用户列表。 一条经验法则是，每月检查谁具有Adobe Commerce应用程序的SSH和管理员访问权限。 如果检测到任何新用户，请禁用其帐户并遵循针对此类事件的任何公司策略和过程。 恢复用户访问比从利用漏洞中恢复更容易。

## 数据库清理

限制对生产数据的访问。 这些指定的队友应能够拉下生产数据库，并清除其真实数据。 如果可以选择删除数据，请截断相应的表，如订单、报价和客户。 但是，有时您需要完整的数据集，但可以匿名处理这些值。 在暂存环境中通常会发生这种情况。 在升级之前，此插件也非常有用。 通过拥有真实的数据量，但匿名化可以确保您测试和验证正确执行部署以进行升级的时间。 如果您的数据集有限，则可能会低估升级过程和时间。

+++随机化客户信息示例
以下示例介绍了如何在Adobe Commerce存储数据的某些标准表中使用随机字符串以及所有名字和姓氏字段更改客户电子邮件地址。 **请记得检查所有表中是否有敏感数据，此列表并非全部包含于可能存储客户数据的表中**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++您还可以截断表，而不是尝试进行匿名处理

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++完全删除信息示例
下面是一个示例，介绍如何在启动之前删除所有订单、报价单、贷项通知单等，或者适用于较低级别的开发环境

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## 使用环境变量

[!BADGE 仅云上的Adobe Commerce]{type=Informative}

使用环境变量有助于您设置特定值，这些值可以也应该针对每个环境进行更改。 例如，您可能希望对每个环境使用不同的管理员URL。 通过将此值设置为环境变量，您能够配置此值，并在必要时从Cloud UI快速引用此值。

有关此主题的更多信息，请参阅云基础架构环境变量上的Experience League[Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## 软件漏洞扫描工具

CI/CD管道可以是一个功能强大的工具，并帮助自动执行某些任务。 特别是，开发人员有机会提交可能被利用的代码，这始终是切实可行的。 对等代码审查通常会捕获此类项目，但由于它是人，因此会发生错误。 自动代码扫描有助于减少新引入的功能中出现意外漏洞的机会。 甚至可以使用这些工具来阻止将代码合并到实时代码库中。 有许多方法和工具可以提供自动代码安全和质量扫描。 可以有强大的自定义开发工具，但它们需要不断更新和调整。 另一种方法是应用主动更新的工具，如synk.io和Amazon的代码检查器。

## Web应用程序防火墙

与DevOps或托管提供商通话时经常使用的Web应用程序防火墙或WAF。

Web应用程序防火墙(WAF)通过根据一组安全规则过滤流量，防止恶意流量进入站点和网络。 触发任何规则的流量会被阻止，以免损害您的网站或网络。

Adobe Commerce的cloud WAF提供了WAF策略和规则集，旨在保护Adobe Commerce Web应用程序免受各种攻击。 如果您选择自托管选项，则您应负责查找WAF和配置规则。 一些托管提供商和WAF提供商具有一组通用规则，这是一个良好的开端，但有一些工作需要让您的项目变得可行。

WAF会检查Web和管理通信以识别任何可疑活动。 它会评估GET和POST流量（HTTP API调用），并应用规则集来确定要阻止的流量。 WAF可以阻止多种攻击，包括SQL注入攻击、跨站点脚本攻击、数据导出攻击以及违反HTTP协议等。

作为基于云的服务，WAF不需要安装或维护任何硬件或软件。 Fastly是一家现有的技术合作伙伴，负责提供软件和专业知识。 它们的高性能、始终可用的WAF驻留在Fastly全球交付网络的每个缓存节点中。

有关Fastly提供的Adobe Commerce on cloud的WAF的更多信息，请阅读[Adobe Commerce知识库常见问题解答](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}。

{{$include /help/_includes/hosting-related-links.md}}
