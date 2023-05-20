---
title: 自行託管Adobe Commerce安全性概念
description: 瞭解自行託管的安全性概念以及要考慮的概念和最佳實務。 瞭解唯讀檔案系統、惡意程式碼掃描等概念，以及託管Adobe Commerce時需考慮的許多其他主題。
landing-page-description: 瞭解自行託管Adobe Commerce時的一些安全性概念及考量事項。
short-description: 瞭解自行託管Adobe Commerce的策略和安全概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# 安全性概念

對於任何與電子商務專案相關的專案，安全性應一律為重要考量。 如果沒有強大的安全防線，可以受到攻擊的表面面積會以指數形式增大。 所提出的概念和構想提供經證實的方法，可降低通常被利用的常見漏洞。

下列概念並沒有任何特定順序。 其目的是為了提供一些想法和概念以供考慮。 其中許多是免費的，或需要最少的設定、設定和後續監視。 在本教學課程之外研究這些主題，以確保您對此處提供的概念有足夠深刻的理解。

## 唯讀檔案系統

唯讀檔案系統概念是借自於 [雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. 這會完全移除不良執行者使用的主要區域。 許多利用漏洞攻擊會更改商務應用程式中預期的檔案，以避免偵測。 這個錯誤的實行者不會建立檔案，而是會變更現有檔案的內容，以執行非預期的動作。 讓檔案系統成為唯讀可大幅減少此攻擊向量。

## 使用TWO Factor驗證和密碼管理員

切勿共用密碼。 每個管理員使用者都應該擁有自己的帳戶，並具有適當的ACL。 確保絕對不會停用或移除兩個因子識別。 如果您提供協力廠商的管理員存取權，請確定密碼是由密碼管理員產生，且永不重複使用。

## 惡意程式碼掃描

惡意程式碼掃描通常可以從嘗試在Adobe Commerce中專門化的託管提供者找到。 隨著新威脅的發現、分類和診斷，這個已知的惡意程式碼和漏洞庫日益增加。 查詢代管提供者是否有這類服務，以及這些服務是否可以自動執行或僅應要求執行。 您也可以訂閱一些服務，使用自己的已知利用漏洞程式庫，持續檢查您的商業應用程式是否有利用漏洞。 其中有些僅供外部使用，有些可新增至基礎架構，提供所有資料夾、檔案甚至資料庫的內部深層掃描。 從Sansec.io到Sucuri，當然還有MageReport，在此領域擁有多年經驗的供應商不勝列舉。 部分為免費，部分則隨附相關費用。 瞭解這一點並與Adobe Commerce架構師和DevOps團隊進行深思熟慮的對話，將確保您找到正確的解決方案。

## 適用於商務的全網站分析工具

此 [全網站分析工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} 是主動式自助服務工具和中央存放庫，其中包含詳細的系統分析和建議，以確保您的Adobe Commerce安裝的安全性和可操作性。 它提供全天候的即時效能監控、報告和建議，以找出潛在問題，並更好地瞭解網站健康狀況、安全性和應用程式設定。 它有助於縮短解析時間，並改善網站穩定性和效能。

## 啟用及驗證管理動作記錄的設定

登入Adobe Commerce管理員並導覽至「商店>設定>進階>管理員>管理員動作記錄」後，即可找到此選項。 這會提供受監視和記錄的事件的清單。 如果懷疑有人取得商務管理員的存取許可權，則在受利用網站上進行鑑證分析時，此功能會很有用。 此記錄和報告有助於檢視不良執行者執行了哪些事件。 如果任何管理員動作記錄被停用，表示有人可能為了遮蓋在執行某些動作時移除記錄。

## 用於ssh存取的Bastion Server

這很難說明安全性概念教學課程中的大部分主題。 其基本構想是提供可作為SSH存取中間人的伺服器。 如此一來，您的生產伺服器絕不允許外部ssh連線。 您可以建立此堡壘伺服器，並使用本機IP遮罩，以確保只允許指定的伺服器透過SSH連線至這些伺服器。

## 檢閱ACL角色和許可權

Adobe Commerce的每位管理員使用者都會獲派ACL角色。 應建立此角色，以僅提供必須執行工作的功能。 應該經常評估ACL角色，以確保它們不會提供超過必要的許可權。 如有需要，請建立多個ACL角色，並賦予其職責。 如果由於某種原因將存取權授予第三方，則應儘快將其停用。 在建立管理員使用者時，詢問他們絕對需要存取權多久並設定自動到期日。

## 經常稽核管理員使用者和SSH使用者存取

若要偵測不需要或未授權的管理員使用者建立，應經常稽核管理員使用者清單。 一個好的經驗法則是，每月檢查誰擁有Adobe Commerce應用程式的SSH和管理員存取權。 如果偵測到任何新使用者，請停用其帳戶，並遵循公司針對這類事件的任何原則和程式。 復原使用者存取權比從利用漏洞復原更容易。

## 資料庫清除

限制對生產資料的存取。 這些指定的隊友應該能夠提取生產資料庫，並清除真實資料。 如果可以移除資料，請截斷適當的表格，例如訂單、報價和客戶。 不過，有時候您會想要完整的資料集，但您可以匿名處理這些值。 在中繼環境中通常會發生這種情況。 在升級之前它也很有用。 透過擁有真實數量的資料，但匿名化可確保您測試和驗證正確執行部署以進行升級的時間。 如果您的資料集有限，可能會低估升級流程和時機。

+++隨機化客戶資訊範例以下範例說明如何在Adobe Commerce儲存資料的某些標準表格中，以隨機字串及所有名字和姓氏欄位變更客戶電子郵件地址。 **請記得檢查所有表格中是否有敏感資料，此清單並非全部包含於可能儲存客戶資料的表格中**

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


+++您也可以截斷表格，而非嘗試匿名處理

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

+++完全移除資訊範例在啟動前或較低開發環境移除所有訂單、報價單、銷退折讓單等專案的範例

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

## 使用環境變數

[!BADGE 僅限雲端上的Adobe Commerce]{type=Informative}

使用環境變數可協助您設定特定值，而這些值可以而且應該針對每個環境變更。 例如，您可能希望每個環境有不同的管理員URL。 透過將此值設定為環境變數，您可以設定此值，並視需要從Cloud UI快速參考此值。

您可以在Experience League中閱讀更多有關本主題的資訊 [雲端基礎結構環境變數上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## 軟體弱點掃描工具

CI/CD管道可以是強大的工具，並幫助自動化某些任務。 尤其是，開發人員有機會提交可能被利用的程式碼，這始終是真實的可能。 同級程式碼審查通常會捕捉此類專案，但由於它是人，所以會發生錯誤。 自動化程式碼掃描有助於減少新推出功能中出現非預期漏洞的機會。 甚至可以使用這些工具來阻止將程式碼合併到即時程式碼基底中。 提供自動化程式碼安全性與品質掃描的方式與工具有很多種。 雖然可以有健全的自訂開發工具，但這些工具確實需要持續更新和調整。 另一種選擇是套用主動更新的工具，例如synk.io和Amazon的程式碼檢查器。

## Web應用程式防火牆

與DevOps或託管提供者通話時通常使用的Web應用程式防火牆或WAF。

Web應用程式防火牆(WAF)會根據一組安全性規則來篩選流量，以防止惡意流量進入網站和網路。 觸發任何規則的流量會在損害您的網站或網路之前遭到封鎖。

Adobe Commerce的雲端WAF提供WAF原則，其中包含專為保護Adobe Commerce Web應用程式免受各種攻擊而設計的規則集。 如果您選擇自行託管選項，則需自行尋找WAF並設定規則。 有些託管提供者和WAF提供者有一組通用規則，這是一個良好的開始，但預計某些工作會幫助您完成專案。

WAF會檢查Web和管理流量，以識別任何可疑活動。 它會評估GET和POST流量（HTTP API呼叫），並套用規則集以決定要封鎖的流量。 WAF可以封鎖各種攻擊，包括SQL插入攻擊、跨網站指令碼攻擊、資料匯出攻擊和HTTP通訊協定違規。

作為雲端型服務，WAF不需要安裝或維護任何硬體或軟體。 Fastly是現有的技術合作夥伴，提供軟體與專業技術。 Fastly的全域傳遞網路的每個快取節點都具備高效能、永不中斷的WAF。

如需Fastly所提供雲端Adobe Commerce上WAF的詳細資訊，請閱讀 [Adobe Commerce知識庫常見問題集](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
