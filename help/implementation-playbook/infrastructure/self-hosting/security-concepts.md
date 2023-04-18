---
title: 自托管Adobe Commerce安全概念
description: 了解自托管安全理念和概念以及要考虑的最佳实践。 了解有关概念，如只读文件系统、恶意软件扫描，以及许多其他主题，以便在托管adobe commerce时加以考虑。
landing-page-description: 了解一些安全概念以及自行托管Adobe Commerce时应考虑的事项。
short-description: 了解自行托管Adobe Commerce的策略和安全概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: cca195c20ddcba634a8fc39c0867e0ae28f43683
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# 安全概念

对于任何与电子商务项目相关的项目，安全应始终是一个强有力的考虑因素。 如果没有强大的安全姿态，可攻击的表面面积将呈指数级增长。 所提出的概念和思想提供了经证实的方法来减少通常利用的常见漏洞。

以下概念不是按特定顺序排列的。 这些建议旨在提供一些需要考虑的想法和概念。 许多设备是免费的，或需要最少的设置和配置以及后续监控。 在本教程之外研究这些主题，确保您对此处提供的概念有足够深入的了解。

## 只读文件系统

只读文件系统概念借用自 [Adobe Commerce云基础架构](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. 这完全删除了坏演员使用的一个主要区域。 许多漏洞利用了更改Commerce应用程序中预期会出现的文件来避免检测。 坏操作程序不会创建一个文件，而是会更改现有文件的内容以执行意外操作。 使文件系统为只读，可显着减少此攻击矢量。

## 使用双因素身份验证和密码管理器

切勿共享密码。 每个管理员用户应拥有自己的帐户，并具有适当的ACL。 确保永远不要禁用或删除两个因素标识。 如果您向第三方提供管理员访问权限，请确保密码由密码管理器生成，且绝不重复使用。

## 恶意软件扫描

通常从尝试专门处理Adobe Commerce的托管提供程序中查找恶意软件扫描。 随着发现、检测和诊断新威胁，这个已知恶意软件和漏洞库越来越多。 查询托管提供商是否具有此类服务，以及这些服务是否可以自动运行，或仅在请求时运行。 您还可以订阅一些服务，这些服务可以使用其自己的已知漏洞库来不断检查您的商务应用程序是否存在漏洞。 其中一些仅是外部的，有些可以添加到基础结构中，以提供所有文件夹、文件甚至数据库的内部深层扫描。 从Sansec.io到Sucuri，当然还有MageReport等几个在这个领域拥有多年经验的提供商。 部分客房免费，部分客房则收取相关费用。 了解此功能可用，并与Adobe Commerce架构师和DevOps团队进行周密的对话，将确保您找到正确的解决方案。

## 适用于商业的站点范围分析工具

的 [站点范围分析工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} 是一款主动式自助服务工具和中央存储库，其中包含详细的系统分析和建议，可确保Adobe Commerce安装的安全性和可操作性。 它提供24/7实时性能监控、报告和建议，以确定潜在问题并更好地了解站点运行状况、安全和应用程序配置。 它有助于缩短解析时间并提高站点稳定性和性能。

## 启用并验证管理操作日志记录的设置

登录Adobe Commerce管理员并导航到商店>配置>高级>管理员>管理员操作日志记录后，即可找到该日志。 这提供了被监控和记录的事件列表。 当对被利用的站点进行法证分析时（如果怀疑他们获得了商务管理员的访问权限），此方法非常有用。 此日志记录和报表有助于查看坏演员执行的事件。 如果禁用了任何管理员操作日志记录，则表示在执行某些操作时，某人可能已禁用这些操作以覆盖该日志记录。

## 用于SSH访问的Bastion Server

这较难解释“安全概念”教程中的大多数主题。 其基本思想是提供充当ssh访问中间人的服务器。 这样，您的生产服务器就永远不允许外部ssh连接。 您可以创建此堡垒服务器，并使用本地IP掩码来确保仅允许指定的服务器通过SSH连接到它们。

## 查看ACL角色和权限

每个Adobe Commerce管理员用户都分配有ACL角色。 应创建此角色，以便仅提供必须执行作业的功能。 应经常评估ACL角色，以确保它们不会提供超出必要权限的权限。 如果需要，请创建许多具有责任的ACL角色。 如果出于某些原因授予第三方访问权限，则应尽快取消激活该第三方。 询问他们在创建管理员用户时绝对需要多长时间的访问权限并设置自动过期日期。

## 频繁审核管理员用户和SSH用户访问

要检测不需要或未授权的管理员用户创建情况，应经常审核管理员用户列表。 一条经验法则是每月检查谁拥有Adobe Commerce应用程序的SSH和管理员访问权限。 如果检测到任何新用户，请禁用其帐户，并遵循此类事件的任何公司策略和程序。 恢复用户访问权限比从利用漏洞中恢复更容易。

## 数据库清理

限制对生产数据的访问。 这些指定的队友应该能够提取生产数据库，并清除其实际数据。 如果可以删除数据，则会截断相应的表，如订单、报价和客户。 但是，有时您希望获得完整的数据集，但值可以匿名化。 在暂存环境中通常是如此。 在升级之前，此功能也非常有用。 通过让实际的数据量，但匿名化可确保您测试并验证正确执行升级部署的时间。 如果您的数据集有限，则可能会低估升级过程和时间。

+++随机化客户信息示例以下示例用于说明如何在Adobe Commerce存储数据的一些标准表中使用随机字符串以及所有名字和姓氏字段更改客户电子邮件地址。 **请记住，要检查所有表中是否有敏感数据，此列表并非全部包含可能存储客户数据的表**

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


+++您还可以截断表，而不是尝试匿名化

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

+++完全删除信息示例以下示例用于在启动之前删除所有订单、报价、贷项通知单等内容，或在较低开发环境中删除这些内容

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

[!BADGE Adobe Commerce（仅限云）]{type=Informative}

通过使用环境变量，您可以设置能够而且应该针对每个环境进行更改的某些值，这对您有所帮助。 例如，您可能希望每个环境具有不同的管理员URL。 通过将此值设置为环境变量，您可以配置此值，并在必要时从云UI中快速引用此值。

您可以在Experience League中阅读有关此主题的更多信息 [云基础架构环境变量上的商务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## 软件漏洞扫描工具

CI/CD管道是一款功能强大的工具，可帮助自动执行某些任务。 特别是，开发人员提交可能可利用的代码的机会始终是实实在在的可能。 同行代码审阅通常会捕获此类项目，但由于它是人类，因此会出错。 自动代码扫描有助于减少新引入功能中出现意外漏洞的机会。 这些工具甚至可以阻止将代码合并到实时代码库中。 提供自动代码安全性和质量扫描的多种方法和工具。 虽然可以使用强大的自定义开发工具，但需要不断更新和调整。 另一种方法是应用主动更新的工具，例如synk.io和Amazon的代码检查器。

## Web应用程序防火墙

与DevOps或托管提供商交谈时通常使用的Web应用程序防火墙或WAF。

Web应用程序防火墙(WAF)通过针对一组安全规则过滤流量来防止恶意流量进入站点和网络。 触发任何规则的流量在损坏您的网站或网络之前会被阻止。

Adobe Commerce的云WAF提供了WAF策略，其中包含一个规则集，旨在保护您的Adobe Commerce Web应用程序免受各种攻击。 如果选择自托管选项，则您负责查找WAF并配置规则。 一些托管提供商和WAF提供商拥有一组通用规则，这是一个良好的开端，但是，您需要完成一些工作来使项目的各项工作正常进行。

WAF检查Web和管理员流量以识别任何可疑活动。 它会评估GET和POST流量（HTTP API调用），并应用规则集以确定要阻止的流量。 WAF可以阻止各种攻击，包括SQL注入攻击、跨站点脚本攻击、数据过滤攻击和HTTP协议违规。

作为基于云的服务，WAF无需安装或维护硬件或软件。 Fastly是现有的技术合作伙伴，提供软件和专业知识。 它们的高性能、始终运行的WAF驻留在Fastly的全局交付网络中的每个缓存节点中。

有关Fastly提供的云上Adobe Commerce上的WAF的更多信息，请阅读 [Adobe Commerce知识库常见问题解答](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
