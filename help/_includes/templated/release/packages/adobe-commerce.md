---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '2906'
ht-degree: 0%

---
# Adobe Commerce包

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce使用编辑器管理PHP包。

`composer.json`文件声明了包的列表，而`composer.lock`文件存储了用于构建Adobe Commerce安装的包的完整列表（每个包的完整版本及其依赖项）。

以下参考文档是从`composer.lock`文件生成的，它涵盖Adobe Commerce 2.4.8中包含的必需包。

## 依赖关系

`magento/product-enterprise-edition 2.4.8`具有以下依赖项：

- adobe-commerce/extensions-metapackage： 2.0.1
- colimollenhour/cache-backend-file： ^1.4
- colimollenhour/cache-backend-redis： ^1.16
- colimollenhour/credis： ^1.15
- colimollenhour/php-redis-session-abstract： ^2.0
- 作者/作者： ^2.0， ！=2.2.16
- duosecurity/duo_api_php： ^1.1
- duosecurity/duo_universal_php： ^1.0
- elasticsearch/elasticsearch： ^8.15
- ext-bcmath： *
- ext-ctype： *
- ext-curl： *
- ext-dom： *
- ext-ftp： *
- ext-gd： *
- ext-hash： *
- ext-iconv： *
- ext-intl： *
- ext-mbstring： *
- ext-openssl： *
- ext-pdo_mysql： *
- ext-simplexml： *
- 外部soap： *
- 分钠：*
- ext-spl： *
- ext-xsl： *
- ext-zip： *
- ezyang/htmlpurifier： ^4.17
- guzzlehttp/guzzle： ^7.5
- laminas/laminas-captcha： ^2.18
- laminas/laminas-code： ^4.13
- laminas/laminas-di： ^3.15
- laminas/laminas-escaper： ^2.13
- laminas/laminas-eventmanager： ^3.11
- 层合板/层合板 — 馈送： ^2.22
- 层合板/层合板滤镜： ^2.33
- laminas/laminas-http： ^2.15
- laminas/laminas-i18n： ^2.17
- laminas/laminas-modulemanager： ^2.11
- laminas/laminas-mvc： ^3.6
- laminas/laminas-permissions-acl： ^2.10
- laminas/laminas-servicemanager： ^3.16
- laminas/laminas-soap： ^2.10
- laminas/laminas-stdlib： ^3.11
- laminas/laminas-uri： ^2.9
- laminas/laminas-validator： ^2.23
- league/flysystem： ^3.0
- league/flysystem-aws-s3-v3： ^3.0
- lib-libxml： *
- magento/composer： ^1.10.1-beta1
- magento/composer-dependency-version-audit-plugin： ^0.1
- magento/framework-foreign-key： 100.4.7
- magento/magento-composer-installer： >=0.4.0
- magento/magento-zf-db： ^3.21
- magento/magento2-ee-base： 2.4.8
- [magento/module-admin-gws](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws/)： 100.4.8
- [magento/module-admin-gws-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-configurable-product/)： 100.4.5
- [magento/module-admin-gws-staging](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-staging/)： 100.4.5
- [magento/module-advanced-catalog](https://developer.adobe.com/commerce/php/module-reference/module-advanced-catalog/)： 100.4.5
- [magento/module-advanced-checkout](https://developer.adobe.com/commerce/php/module-reference/module-advanced-checkout/)： 100.4.8
- [magento/module-advanced-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-rule/)： 100.4.5
- [magento/module-advanced-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-sales-rule/)： 100.4.5
- [magento/module-application-server](https://developer.adobe.com/commerce/php/module-reference/module-application-server/)： 100.4.1
- [magento/module-application-server-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-server-new-relic/)： 100.4.1
- [magento/module-application-server-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-performance-monitor/)： 100.4.1
- [magento/module-application-server-state-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor/)： 100.4.1
- [magento/module-application-server-state-monitor-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor-graph-ql/)： 100.4.1
- [magento/module-async-order](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)： 100.4.4
- [magento/module-async-order-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-async-order-graph-ql/)： 100.4.3
- [magento/module-aws-s3-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-customer-custom-attributes/)： 100.4.5
- [magento/module-aws-s3-gift-card-import-export](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-gift-card-import-export/)： 100.4.5
- [magento/module-aws-s3-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-scheduled-import-export/)： 100.4.5
- [magento/module-banner](https://developer.adobe.com/commerce/php/module-reference/module-banner/)： 101.2.8
- [magento/module-banner-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-banner-customer-segment/)： 100.4.6
- [magento/module-banner-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-banner-graph-ql/)： 100.4.4
- [magento/module-banner-staging](https://developer.adobe.com/commerce/php/module-reference/module-banner-staging/)： 100.4.2
- [magento/module-bundle-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export-staging/)： 100.4.5
- [magento/module-bundle-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-staging/)： 100.4.8
- [magento/module-catalog-event](https://developer.adobe.com/commerce/php/module-reference/module-catalog-event/)： 101.1.7
- [magento/module-catalog-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export-staging/)： 100.4.5
- [magento/module-catalog-inventory-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-staging/)： 100.4.6
- [magento/module-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions/)： 100.4.8
- [magento/module-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions-graph-ql/)： 100.4.6
- [magento/module-catalog-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-staging/)： 100.4.8
- [magento/module-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging/)： 100.4.8
- [magento/module-catalog-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging-graph-ql/)： 100.4.7
- [magento/module-catalog-url-rewrite-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-staging/)： 100.4.7
- [magento/module-checkout-address-search](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search/)： 100.4.7
- [magento/module-checkout-address-search-gift-registry](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search-gift-registry/)： 100.4.4
- [magento/module-checkout-staging](https://developer.adobe.com/commerce/php/module-reference/module-checkout-staging/)： 100.4.7
- [magento/module-cms-staging](https://developer.adobe.com/commerce/php/module-reference/module-cms-staging/)： 100.4.8
- [magento/module-configurable-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-staging/)： 100.4.7
- [magento/module-custom-attribute-management](https://developer.adobe.com/commerce/php/module-reference/module-custom-attribute-management/)： 100.4.7
- [magento/module-customer-balance](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance/)： 100.4.8
- [magento/module-customer-balance-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance-graph-ql/)： 100.4.5
- [magento/module-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes/)： 100.4.8
- [magento/module-customer-custom-attributes-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes-graph-ql/)： 100.4.1
- [magento/module-customer-finance](https://developer.adobe.com/commerce/php/module-reference/module-customer-finance/)： 100.4.5
- [magento/module-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment/)： 102.1.8
- [magento/module-customer-segment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment-graph-ql/)： 100.4.1
- [magento/module-deferred-total-calculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/)： 100.4.3
- [magento/module-downloadable-staging](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-staging/)： 100.4.7
- [magento/module-elasticsearch-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions/)： 100.4.4
- [magento/module-elasticsearch-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions-graph-ql/)： 100.4.3
- [magento/module-enterprise](https://developer.adobe.com/commerce/php/module-reference/module-enterprise/)： 100.4.6
- [magento/module-gift-card](https://developer.adobe.com/commerce/php/module-reference/module-gift-card/)： 101.3.8
- [magento/module-gift-card-account](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account/)： 101.2.8
- [magento/module-gift-card-account-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account-graph-ql/)： 100.4.6
- [magento/module-gift-card-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-graph-ql/)： 100.4.8
- [magento/module-gift-card-import-export](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-import-export/)： 100.4.5
- [magento/module-gift-card-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-staging/)： 100.4.5
- [magento/module-gift-message-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-staging/)： 100.4.5
- [magento/module-gift-registry](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry/)： 101.2.8
- [magento/module-gift-registry-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry-graph-ql/)： 100.4.4
- [magento/module-gift-wrapping](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping/)： 101.2.7
- [magento/module-gift-wrapping-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-graph-ql/)： 100.4.5
- [magento/module-gift-wrapping-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-staging/)： 100.4.5
- [magento/module-google-optimizer-staging](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer-staging/)： 100.4.5
- [magento/module-google-tag-manager](https://developer.adobe.com/commerce/php/module-reference/module-google-tag-manager/)： 100.4.8
- [magento/module-grouped-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-staging/)： 100.4.6
- [magento/module-import-csv](https://developer.adobe.com/commerce/php/module-reference/module-import-csv/)： 100.4.2
- [magento/module-import-csv-api](https://developer.adobe.com/commerce/php/module-reference/module-import-csv-api/)： 100.4.2
- [magento/module-import-json](https://developer.adobe.com/commerce/php/module-reference/module-import-json/)： 100.4.1
- [magento/module-import-json-api](https://developer.adobe.com/commerce/php/module-reference/module-import-json-api/)： 100.4.1
- [magento/module-invitation](https://developer.adobe.com/commerce/php/module-reference/module-invitation/)： 100.4.7
- [magento/module-layered-navigation-staging](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation-staging/)： 100.4.5
- [magento/module-logging](https://developer.adobe.com/commerce/php/module-reference/module-logging/)： 101.2.8
- [magento/module-login-as-customer-logging](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-logging/)： 100.4.8
- [magento/module-login-as-customer-website-restriction](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-website-restriction/)： 100.4.6
- [magento/module-media-content-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog-staging/)： 100.4.5
- [magento/module-msrp-staging](https://developer.adobe.com/commerce/php/module-reference/module-msrp-staging/)： 100.4.6
- [magento/module-multicoupon](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon/)： 100.4.1
- [magento/module-multicoupon-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-graph-ql/)： 100.4.1
- [magento/module-multicoupon-ui](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-ui/)： 100.4.1
- [magento/module-multiple-wishlist](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist/)： 100.4.8
- [magento/module-multiple-wishlist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist-graph-ql/)： 100.4.4
- [magento/module-payment-staging](https://developer.adobe.com/commerce/php/module-reference/module-payment-staging/)： 100.4.5
- [magento/module-persistent-history](https://developer.adobe.com/commerce/php/module-reference/module-persistent-history/)： 100.4.5
- [magento/module-price-permissions](https://developer.adobe.com/commerce/php/module-reference/module-price-permissions/)： 100.4.4
- [magento/module-product-video-staging](https://developer.adobe.com/commerce/php/module-reference/module-product-video-staging/)： 100.4.5
- [magento/module-promotion-permissions](https://developer.adobe.com/commerce/php/module-reference/module-promotion-permissions/)： 100.4.5
- [magento/module-quote-commerce-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-commerce-graph-ql/)： 100.4.1
- [magento/module-quote-gift-card-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-gift-card-options/)： 100.4.5
- [magento/module-quote-staging](https://developer.adobe.com/commerce/php/module-reference/module-quote-staging/)： 100.4.5
- [magento/module-reminder](https://developer.adobe.com/commerce/php/module-reference/module-reminder/)： 101.2.7
- [magento/module-remote-storage-commerce](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage-commerce/)： 100.4.4
- [magento/module-resource-connections](https://developer.adobe.com/commerce/php/module-reference/module-resource-connections/)： 100.4.5
- [magento/module-review-staging](https://developer.adobe.com/commerce/php/module-reference/module-review-staging/)： 100.4.5
- [magento/module-reward](https://developer.adobe.com/commerce/php/module-reference/module-reward/)： 101.2.8
- [magento/module-reward-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-reward-graph-ql/)： 100.4.7
- [magento/module-reward-staging](https://developer.adobe.com/commerce/php/module-reference/module-reward-staging/)： 100.4.5
- [magento/module-rma](https://developer.adobe.com/commerce/php/module-reference/module-rma/)： 101.2.8
- [magento/module-rma-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-rma-graph-ql/)： 100.4.7
- [magento/module-rma-staging](https://developer.adobe.com/commerce/php/module-reference/module-rma-staging/)： 100.4.5
- [magento/module-sales-archive](https://developer.adobe.com/commerce/php/module-reference/module-sales-archive/)： 101.0.6
- [magento/module-sales-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-staging/)： 100.4.7
- [magento/module-scalable-checkout](https://developer.adobe.com/commerce/php/module-reference/module-scalable-checkout/)： 100.4.7
- [magento/module-scalable-inventory](https://developer.adobe.com/commerce/php/module-reference/module-scalable-inventory/)： 100.4.6
- [magento/module-scalable-oms](https://developer.adobe.com/commerce/php/module-reference/module-scalable-oms/)： 100.4.6
- [magento/module-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-scheduled-import-export/)： 101.2.8
- [magento/module-search-staging](https://developer.adobe.com/commerce/php/module-reference/module-search-staging/)： 100.4.6
- [magento/module-staging](https://developer.adobe.com/commerce/php/module-reference/module-staging/)： 101.2.8
- [magento/module-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-staging-graph-ql/)： 100.4.5
- [magento/module-support](https://developer.adobe.com/commerce/php/module-reference/module-support/)： 101.2.7
- [magento/module-swat](https://developer.adobe.com/commerce/php/module-reference/module-swat/)： 100.4.6
- [magento/module-target-rule](https://developer.adobe.com/commerce/php/module-reference/module-target-rule/)： 101.2.8
- [magento/module-target-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-target-rule-graph-ql/)： 100.4.5
- [magento/module-versions-cms](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms/)： 101.2.8
- [magento/module-versions-cms-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-page-cache/)： 100.4.4
- [magento/module-versions-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite/)： 100.4.6
- [magento/module-versions-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite-graph-ql/)： 100.4.4
- [magento/module-visual-merchandiser](https://developer.adobe.com/commerce/php/module-reference/module-visual-merchandiser/)： 100.4.8
- [magento/module-webapi-rest-gws](https://developer.adobe.com/commerce/php/module-reference/module-webapi-rest-gws/)： 100.4.0
- [magento/module-website-restriction](https://developer.adobe.com/commerce/php/module-reference/module-website-restriction/)： 100.4.7
- [magento/module-weee-staging](https://developer.adobe.com/commerce/php/module-reference/module-weee-staging/)： 100.4.5
- [magento/module-wishlist-gift-card](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card/)： 100.4.4
- [magento/module-wishlist-gift-card-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card-graph-ql/)： 100.4.4
- magento/page-builder-commerce： 1.7.5
- magento/product-community-edition： 2.4.8
- magento/security-package-ee： 1.0.3
- magento/theme-adminhtml-spectrum： 100.4.3
- magento/zend-cache： ^1.16
- magento/zend-db： ^1.16
- magento/zend-pdf： ^1.16
- 独白/独白： ^3.6
- opensearch-project/opensearch-php： ^2.3
- pelago/表情符号： ^7.0
- php： ~8.2.0||~8.3.0||~8.4.0
- php-amqplib/php-amqplib： ^3.2
- phpseclib/mcrypt_compat： ^2.0
- phpseclib/phpseclib： ^3.0
- psr/日志： ^2 || ^3
- ramsey/uuid： ^4.2
- 交响曲/控制台： ^6.4
- symfony/intl： ^6.4
- 交响曲/邮件程序： ^6.4
- symfony/mime： ^6.4
- 交响曲/处理： ^6.4
- symfony/字符串： ^6.4
- tedivm/jshrink： ^1.4
- tubalmartin/cssmin： ^4.1
- web-token/jwt-framework： ^3.4
- webonyx/graphql-php： ^15.0
- wikimedia/less.php： ^5.0

## 第三方许可证

### Apache-2.0，仅LGPL-2.1

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
    </td>
    <td>库</td>
    <td>适用于OpenSearch的PHP客户端</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>库</td>
    <td>Adobe Stock API库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>库</td>
    <td>适用于PHP的AWS公共运行时</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>库</td>
    <td>适用于PHP的AWS SDK — 在PHP项目中使用Amazon Web Services</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">开放遥测/api</a>
    </td>
    <td>库</td>
    <td>适用于OpenTelemetry PHP的API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">开放遥测/上下文</a>
    </td>
    <td>库</td>
    <td>OpenTelemetry PHP的上下文实现。</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>中继包</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
    </td>
    <td>库</td>
    <td>LESS处理器的PHP端口</td>
  </tr>
  </tbody>
</table>

### BSD-2子句

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode">培根/培根 — qr-code</a>
    </td>
    <td>库</td>
    <td>BaconQrCode是PHP的二维码生成器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">dasprid/enum</a>
    </td>
    <td>库</td>
    <td>PHP 7.1枚举实现</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">webimpress/safe-writer</a>
    </td>
    <td>库</td>
    <td>用于安全写入文件的工具，以避免出现争用情况</td>
  </tr>
  </tbody>
</table>

### BSD-3 — 子句

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colimollenhour/cache-backend-file</a>
    </td>
    <td>Magento-module</td>
    <td>库存Zend_Cache_Backend_File后端在标记清理方面的性能非常差，导致其随着缓存项目数的增加而变得不可用。 此后端进行了许多更改，从而极大地提高了性能，尤其是在标签清理方面。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colimollenhour/php-redis-session-abstract</a>
    </td>
    <td>库</td>
    <td>具有乐观锁定的基于Redis的会话处理程序</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>库</td>
    <td>Duo Universal SDK的PHP实现。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">firebase/php-jwt</a>
    </td>
    <td>库</td>
    <td>在PHP中编码和解码JSON Web令牌(JWT)的简单库。 应符合当前规范。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>库</td>
    <td>使用Figlet、图像、ReCaptcha等生成和验证CAPTCHA</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">laminas/laminas-code</a>
    </td>
    <td>库</td>
    <td>PHP Reflection API、静态代码扫描和代码生成的扩展</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>库</td>
    <td>提供了基于嵌套对象属性的用户界面，用于访问应用程序代码中的此配置数据</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">层叠/层叠 — di</a>
    </td>
    <td>库</td>
    <td>PSR-11容器的自动依赖项注入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">laminas/laminas-escaper</a>
    </td>
    <td>库</td>
    <td>安全可靠地转义HTML、HTML属性、JavaScript、CSS和URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventmanager</a>
    </td>
    <td>库</td>
    <td>触发和侦听PHP应用程序中的事件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">层叠/层叠 — 馈送</a>
    </td>
    <td>库</td>
    <td>提供创建和使用RSS和Atom馈送的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">层叠/层叠 — 筛选</a>
    </td>
    <td>库</td>
    <td>以编程方式过滤和标准化数据和文件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>库</td>
    <td>提供用于执行超文本传输协议(HTTP)请求的轻松界面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">laminas/laminas-i18n</a>
    </td>
    <td>库</td>
    <td>为您的应用程序提供翻译，并筛选和验证国际化值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>库</td>
    <td>提供了将本机PHP序列化为JSON并将JSON解码为本机PHP的方便方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">laminas/laminas-loader</a>
    </td>
    <td>库</td>
    <td>自动加载和插件加载策略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>库</td>
    <td>用于层板MVC应用的模块化应用系统</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">laminas/laminas-mvc</a>
    </td>
    <td>库</td>
    <td>Laminas的事件驱动MVC层，包括MVC应用程序、控制器和插件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>库</td>
    <td>为权限管理提供轻量级和灵活的访问控制列表(ACL)实施</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-recaptcha</a>
    </td>
    <td>库</td>
    <td>ReCaptcha Web服务的OOP包装器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas路由器</a>
    </td>
    <td>库</td>
    <td>适用于HTTP和控制台应用程序的灵活路由系统</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">laminas/laminas-server</a>
    </td>
    <td>库</td>
    <td>创建基于反射的RPC服务器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-servicemanager</a>
    </td>
    <td>库</td>
    <td>工厂驱动的依赖项注入容器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas会话</a>
    </td>
    <td>库</td>
    <td>面向PHP会话和存储对象的接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">laminas/laminas-soap</a>
    </td>
    <td>库</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>库</td>
    <td>SPL扩展、数组实用程序、错误处理程序等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>库</td>
    <td>创建FIGlet和基于文本的表</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>库</td>
    <td>laminas-i18n的Translator组件的接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>库</td>
    <td>帮助处理和验证“统一资源标识符(URI)”的组件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>库</td>
    <td>适用于多种域的验证类，以及链式验证器以创建复杂验证标准的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>库</td>
    <td>支持并提供多个视图层、辅助器等的柔性视图层</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>库</td>
    <td>使用本机PHP简单、快速地实施枚举</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>库</td>
    <td>用PHP编写的PHP解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/recaptcha</a>
    </td>
    <td>库</td>
    <td>适用于Google的reCAPTCHA for PHP 8.4及更高版本的客户端库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jshrink</a>
    </td>
    <td>库</td>
    <td>PHP中内置的Javascript小型器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
    </td>
    <td>库</td>
    <td>YUI CSS压缩器的PHP端口</td>
  </tr>
  </tbody>
</table>

### BSD-3 — 子句修改

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colimollenhour/cache-backend-redis</a>
    </td>
    <td>Magento-module</td>
    <td>使用Redis的Zend_Cache后端，完全支持标记。</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat">paragonie/na_compat</a>
    </td>
    <td>库</td>
    <td>纯PHP的libna实现；使用PHP扩展（如果存在）</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1或更高版本

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlpurifier</a>
    </td>
    <td>库</td>
    <td>使用PHP编写的符合标准的HTML过滤器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
    </td>
    <td>库</td>
    <td>以前称为videlalvaro/php-amqplib。  此库是AMQP协议的纯PHP实现。 已经通过RabbitMQ的测试。</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php">braintree/braintree_php</a>
    </td>
    <td>库</td>
    <td>Braintree PHP客户端库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math">程序块/数学</a>
    </td>
    <td>库</td>
    <td>任意精度算术库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">程序块/varexporter</a>
    </td>
    <td>库</td>
    <td>var_export()的强大替代函数可以导出不带__set_state()的关闭项和对象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">christian-riesen/base32</a>
    </td>
    <td>库</td>
    <td>根据RFC 4648的Base32编码器/解码器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colimollenhour/credis</a>
    </td>
    <td>库</td>
    <td>Credis是Redis键值存储的轻型接口，当可用时它会封装phpredis库以提高性能。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle">composer/ca-bundle</a>
    </td>
    <td>库</td>
    <td>允许您查找系统CA捆绑包的路径，并包括对Mozilla CA捆绑包的回退。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">composer/class-map-generator</a>
    </td>
    <td>库</td>
    <td>用于扫描PHP代码并生成类映射的实用程序。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer">作曲家/作曲家</a>
    </td>
    <td>库</td>
    <td>Composer可帮助您声明、管理和安装PHP项目的依赖项。 它可确保您随时随地拥有正确的栈栈。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">composer/metadata-minifier</a>
    </td>
    <td>库</td>
    <td>处理元数据缩小和扩展的小型实用工具库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre">作曲家/密码</a>
    </td>
    <td>库</td>
    <td>提供类型安全预浸料_*替换的PCRE包装库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver">composer/semver</a>
    </td>
    <td>库</td>
    <td>提供实用程序、版本约束解析和验证的服务器库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses">composer/spdx-licenses</a>
    </td>
    <td>库</td>
    <td>SPDX许可证列表和验证库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">composer/xdebug-handler</a>
    </td>
    <td>库</td>
    <td>在不使用Xdebug的情况下重新启动进程。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">理论/词法分析器</a>
    </td>
    <td>库</td>
    <td>PHP Doctrine Lexer分析器库，可在自上而下的递归后代分析器中使用。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">egulias/email-validator</a>
    </td>
    <td>库</td>
    <td>用于针对多个RFC验证电子邮件的库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">弹性/传输</a>
    </td>
    <td>库</td>
    <td>用于弹性产品的HTTP传输PHP库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>库</td>
    <td>适用于Elasticsearch的PHP客户端</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>库</td>
    <td>Endroid二维码</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>库</td>
    <td>用于elasticsearch-php的guzzle/streams（已放弃）分支</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>库</td>
    <td>与elasticsearch-php一起使用的guzzle/RingPHP（已放弃）分支</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>库</td>
    <td>Guzzle是一个PHP HTTP客户端库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promise</a>
    </td>
    <td>库</td>
    <td>Guzzle promise库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>库</td>
    <td>PSR-7消息实施，其中也提供常用实用工具方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">justinrainbow/json-schema</a>
    </td>
    <td>库</td>
    <td>用于验证json架构的库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem">联盟/飞行系统</a>
    </td>
    <td>库</td>
    <td>PHP的文件存储抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">league/flysystem-aws-s3-v3</a>
    </td>
    <td>库</td>
    <td>适用于Flysystem的AWS S3文件系统适配器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">league/flysystem-local</a>
    </td>
    <td>库</td>
    <td>用于Flysystem的本地文件系统适配器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">league/mime-type-detection</a>
    </td>
    <td>库</td>
    <td>用于飞行系统的MIME类型检测</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">monolog/monolog</a>
    </td>
    <td>库</td>
    <td>将日志发送到文件、套接字、收件箱、数据库和各种Web服务</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>库</td>
    <td>以声明方式指定如何从JSON文档中提取元素</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>库</td>
    <td>RFC 4648编码的恒定时间实施(Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>库</td>
    <td>PHP 7中的random_bytes()和random_int()的PHP 5.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/表情符号</a>
    </td>
    <td>库</td>
    <td>将CSS样式转换为HTML代码中的内联样式属性</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-plugin</td>
    <td>查找并安装PSR-7、PSR-17、PSR-18和HTTPlug实施</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>库</td>
    <td>HTTPlug，PHP的HTTP客户端抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">php-http/promise</a>
    </td>
    <td>库</td>
    <td>用于异步HTTP请求的Promise</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>库</td>
    <td>将CSS选择器转换为XPath查询。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>库</td>
    <td>新版DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>库</td>
    <td>属性访问器和变体函数。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>库</td>
    <td>用于mcrypt扩展的PHP 5.x-8.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>库</td>
    <td>PHP安全通信库 — RSA、AES、SSH2、SFTP、X.509等的纯PHP实现。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">psr/缓存</a>
    </td>
    <td>库</td>
    <td>缓存库的通用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">psr/时钟</a>
    </td>
    <td>库</td>
    <td>用于读取时钟的通用接口。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">psr/容器</a>
    </td>
    <td>库</td>
    <td>公共容器接口（PHP图PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">psr/event-dispatcher</a>
    </td>
    <td>库</td>
    <td>用于事件处理的标准接口。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">psr/http-client</a>
    </td>
    <td>库</td>
    <td>HTTP客户端的通用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">psr/http-factory</a>
    </td>
    <td>库</td>
    <td>PSR-17：PSR-7 HTTP消息工厂的通用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">psr/http-message</a>
    </td>
    <td>库</td>
    <td>HTTP消息的通用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">psr/log</a>
    </td>
    <td>库</td>
    <td>用于记录库的通用界面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">ralouphie/getallheaders</a>
    </td>
    <td>库</td>
    <td>getalleaders的polyfill。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection">拉姆齐/收藏集</a>
    </td>
    <td>库</td>
    <td>用于表示和处理收藏集的PHP库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid">ramsey/uuid</a>
    </td>
    <td>库</td>
    <td>用于生成和使用通用唯一标识符(UUID)的PHP库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">react/promise</a>
    </td>
    <td>库</td>
    <td>CommonJS Promise/A for PHP的轻量级实现</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>库</td>
    <td>以PHP编写的CSS文件的解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>库</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>库</td>
    <td>PHAR文件格式实用程序，用于当PHP向上</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">seld/signal-handler</a>
    </td>
    <td>库</td>
    <td>简单的unix信号处理程序在信号不受支持时静默失败，从而易于跨平台开发</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>库</td>
    <td>PHP的AES密钥换行。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>库</td>
    <td>用于根据RFC 4226（HOTP算法）和RFC 6238（TOTP算法）生成一次性密码并与Google身份验证器兼容的PHP库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>库</td>
    <td>用于管理公钥基础结构的PHP框架。 它包括X.509公钥证书、属性证书、证书请求和证书路径验证。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>库</td>
    <td>帮助您查找、加载、组合、自动填写和验证任何类型的配置值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">交响乐/控制台</a>
    </td>
    <td>库</td>
    <td>轻松创建美观且可测试的命令行界面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-selector</a>
    </td>
    <td>库</td>
    <td>将CSS选择器转换为XPath表达式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">symfony/依赖项注入</a>
    </td>
    <td>库</td>
    <td>允许您标准化并集中处理应用程序中构建对象的方式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">symfony/弃用合同</a>
    </td>
    <td>库</td>
    <td>用于触发弃用通知的通用函数和约定</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>库</td>
    <td>提供用于管理错误和轻松调试PHP代码的工具</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>库</td>
    <td>提供一些工具，这些工具允许应用程序组件通过调度事件并监听事件来相互通信</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">symfony/event-dispatcher-contracts</a>
    </td>
    <td>库</td>
    <td>与调度事件相关的一般抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/文件系统</a>
    </td>
    <td>库</td>
    <td>为文件系统提供基本实用程序</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>库</td>
    <td>通过直观的流畅界面查找文件和目录</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>库</td>
    <td>提供功能强大的方法来同步或异步获取HTTP资源</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">symfony/http-client-contract</a>
    </td>
    <td>库</td>
    <td>与HTTP客户端相关的一般抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>库</td>
    <td>为HTTP规范定义面向对象的层</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>库</td>
    <td>提供将请求转换为响应的结构化流程</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>库</td>
    <td>提供对ICU库本地化数据的访问</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">symfony/mailer</a>
    </td>
    <td>库</td>
    <td>帮助发送电子邮件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>库</td>
    <td>允许处理MIME消息</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-ctype</a>
    </td>
    <td>库</td>
    <td>用于CTYPE函数的交感聚合填料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>库</td>
    <td>用于Intl的图形素_*函数的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>库</td>
    <td>用于intl的idn_to_ascii和idn_to_utf8函数的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>库</td>
    <td>Intl的Normalizer类和相关函数的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>库</td>
    <td>Mbstring扩展的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 7.3+功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 8.0及更高版本功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 8.1+功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 8.2+功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 8.3+功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">symfony/进程</a>
    </td>
    <td>库</td>
    <td>执行子进程中的命令</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">交响曲/服务合同</a>
    </td>
    <td>库</td>
    <td>与写入服务相关的一般抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symfony/字符串</a>
    </td>
    <td>库</td>
    <td>为字符串提供面向对象的API，并以统一的方式处理字节、UTF-8代码点和图形集群</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>库</td>
    <td>提供用于浏览任意PHP变量的机制</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-exporter</a>
    </td>
    <td>库</td>
    <td>允许将任何可序列化的PHP数据结构导出为纯PHP代码</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>库</td>
    <td>加载和转储YAML文件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">web-token/jwt-framework</a>
    </td>
    <td>Symfony捆绑包</td>
    <td>PHP和Symfony捆绑包的JSON对象签名和加密库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
    </td>
    <td>库</td>
    <td>GraphQL参考实现的PHP端口</td>
  </tr>
  </tbody>
</table>

### OSL-3.0、AFL-3.0

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>Magento2模块</td>
    <td>不适用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>Magento2模块</td>
    <td>不适用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>Magento2模块</td>
    <td>不适用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>Magento2模块</td>
    <td>不适用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Magento2模块</td>
    <td>不适用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-reward
    </td>
    <td>Magento2模块</td>
    <td>不适用</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
    </td>
    <td>库</td>
    <td>PHP的CBOR编码器</td>
  </tr>
  </tbody>
</table>

### 专有

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### proprietary

<table>
  <thead>
    <tr>
      <th>名称</th>
      <th>类型</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>Magento2模块</td>
    <td>从Gene Commerce为PayPal撰写的Magento Braintree 2.2.0模块创建分支。</td>
  </tr>
  </tbody>
</table>
