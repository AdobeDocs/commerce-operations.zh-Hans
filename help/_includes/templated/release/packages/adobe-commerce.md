---
source-git-commit: 177f301802e1ab1d0560ee98594b8128440efa7c
workflow-type: tm+mt
source-wordcount: '2378'
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

Adobe Commerce使用Composer管理PHP包。

此 `composer.json` 文件声明包的列表，而 `composer.lock` file存储用于构建Adobe Commerce或Magento Open Source安装的软件包（每个软件包及其依赖项的完整版本）的完整列表。

以下参考文档是从 `composer.lock` 它涵盖Adobe Commerce 2.4.6-beta2中包含的必需包。

## 依赖关系

`magento/product-enterprise-edition 2.4.6-beta2` 具有以下依赖关系：

```config
adobe-commerce/saas-metapackage: ~1.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.14
colinmollenhour/credis: ^1.13
colinmollenhour/php-redis-session-abstract: ^1.5
composer/composer: ^2.0, !=2.2.16
elasticsearch/elasticsearch: ^7.17||^8.5
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.14
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ^4.5
laminas/laminas-db: ^2.15
laminas/laminas-di: ^3.7
laminas/laminas-escaper: ^2.10
laminas/laminas-eventmanager: ^3.5
laminas/laminas-feed: ^2.17
laminas/laminas-file: ^2.11
laminas/laminas-filter: ^2.17
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.3
laminas/laminas-oauth: ^2.4
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.11
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.9.0-beta2
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework-foreign-key: 100.4.5-beta2
magento/magento-composer-installer: >=0.4.0-beta1
magento/magento2-ee-base: 2.4.6-beta2
magento/module-admin-gws: 100.4.6-beta2
magento/module-admin-gws-configurable-product: 100.4.3-beta2
magento/module-admin-gws-staging: 100.4.3-beta2
magento/module-advanced-catalog: 100.4.3-beta2
magento/module-advanced-checkout: 100.4.6-beta2
magento/module-advanced-rule: 100.4.3-beta2
magento/module-advanced-sales-rule: 100.4.3-beta2
magento/module-async-order: 100.4.2-beta2
magento/module-async-order-graph-ql: 100.4.1-beta2
magento/module-aws-s3-customer-custom-attributes: 100.4.3-beta2
magento/module-aws-s3-gift-card-import-export: 100.4.3-beta2
magento/module-aws-s3-scheduled-import-export: 100.4.3-beta2
magento/module-banner: 101.2.6-beta2
magento/module-banner-customer-segment: 100.4.4-beta2
magento/module-banner-graph-ql: 100.4.2-beta2
magento/module-banner-staging: 100.4.0-beta2
magento/module-bundle-import-export-staging: 100.4.3-beta2
magento/module-bundle-staging: 100.4.6-beta2
magento/module-catalog-event: 101.1.5-beta2
magento/module-catalog-import-export-staging: 100.4.3-beta2
magento/module-catalog-inventory-staging: 100.4.4-beta2
magento/module-catalog-permissions: 100.4.6-beta2
magento/module-catalog-permissions-graph-ql: 100.4.4-beta2
magento/module-catalog-rule-staging: 100.4.6-beta2
magento/module-catalog-staging: 100.4.6-beta2
magento/module-catalog-staging-graph-ql: 100.4.5-beta2
magento/module-catalog-url-rewrite-staging: 100.4.5-beta2
magento/module-checkout-address-search: 100.4.5-beta2
magento/module-checkout-address-search-gift-registry: 100.4.2-beta2
magento/module-checkout-staging: 100.4.5-beta2
magento/module-cms-staging: 100.4.6-beta2
magento/module-configurable-product-staging: 100.4.5-beta2
magento/module-custom-attribute-management: 100.4.5-beta2
magento/module-customer-balance: 100.4.6-beta2
magento/module-customer-balance-graph-ql: 100.4.3-beta2
magento/module-customer-custom-attributes: 100.4.6-beta2
magento/module-customer-finance: 100.4.3-beta2
magento/module-customer-segment: 102.1.6-beta2
magento/module-deferred-total-calculating: 100.4.1-beta2
magento/module-downloadable-staging: 100.4.5-beta2
magento/module-elasticsearch-catalog-permissions: 100.4.2-beta2
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.1-beta2
magento/module-enterprise: 100.4.4-beta2
magento/module-gift-card: 101.3.6-beta2
magento/module-gift-card-account: 101.2.6-beta2
magento/module-gift-card-account-graph-ql: 100.4.4-beta2
magento/module-gift-card-graph-ql: 100.4.6-beta2
magento/module-gift-card-import-export: 100.4.3-beta2
magento/module-gift-card-staging: 100.4.3-beta2
magento/module-gift-message-staging: 100.4.3-beta2
magento/module-gift-registry: 101.2.6-beta2
magento/module-gift-registry-graph-ql: 100.4.2-beta2
magento/module-gift-wrapping: 101.2.5-beta2
magento/module-gift-wrapping-graph-ql: 100.4.3-beta2
magento/module-gift-wrapping-staging: 100.4.3-beta2
magento/module-google-optimizer-staging: 100.4.3-beta2
magento/module-google-tag-manager: 100.4.6-beta2
magento/module-grouped-product-staging: 100.4.4-beta2
magento/module-import-csv: 100.4.0-beta2
magento/module-import-csv-api: 100.4.0-beta2
magento/module-invitation: 100.4.5-beta2
magento/module-layered-navigation-staging: 100.4.3-beta2
magento/module-logging: 101.2.6-beta2
magento/module-login-as-customer-logging: 100.4.6-beta2
magento/module-login-as-customer-website-restriction: 100.4.4-beta2
magento/module-media-content-catalog-staging: 100.4.3-beta2
magento/module-msrp-staging: 100.4.4-beta2
magento/module-multiple-wishlist: 100.4.6-beta2
magento/module-multiple-wishlist-graph-ql: 100.4.2-beta2
magento/module-payment-staging: 100.4.3-beta2
magento/module-persistent-history: 100.4.3-beta2
magento/module-price-permissions: 100.4.2-beta2
magento/module-product-video-staging: 100.4.3-beta2
magento/module-promotion-permissions: 100.4.3-beta2
magento/module-quote-gift-card-options: 100.4.3-beta2
magento/module-quote-staging: 100.4.3-beta2
magento/module-reminder: 101.2.5-beta2
magento/module-remote-storage-commerce: 100.4.2-beta2
magento/module-resource-connections: 100.4.3-beta2
magento/module-review-staging: 100.4.3-beta2
magento/module-reward: 101.2.6-beta2
magento/module-reward-graph-ql: 100.4.5-beta2
magento/module-reward-staging: 100.4.3-beta2
magento/module-rma: 101.2.6-beta2
magento/module-rma-graph-ql: 100.4.5-beta2
magento/module-rma-staging: 100.4.3-beta2
magento/module-sales-archive: 101.0.4-beta2
magento/module-sales-rule-staging: 100.4.5-beta2
magento/module-scalable-checkout: 100.4.5-beta2
magento/module-scalable-inventory: 100.4.4-beta2
magento/module-scalable-oms: 100.4.4-beta2
magento/module-scheduled-import-export: 101.2.6-beta2
magento/module-search-staging: 100.4.4-beta2
magento/module-staging: 101.2.6-beta2
magento/module-staging-graph-ql: 100.4.3-beta2
magento/module-support: 101.2.5-beta2
magento/module-swat: 100.4.4-beta2
magento/module-target-rule: 101.2.6-beta2
magento/module-target-rule-graph-ql: 100.4.3-beta2
magento/module-versions-cms: 101.2.6-beta2
magento/module-versions-cms-page-cache: 100.4.2-beta2
magento/module-versions-cms-url-rewrite: 100.4.4-beta2
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.2-beta2
magento/module-visual-merchandiser: 100.4.6-beta2
magento/module-website-restriction: 100.4.5-beta2
magento/module-weee-staging: 100.4.3-beta2
magento/module-wishlist-gift-card: 100.4.2-beta2
magento/module-wishlist-gift-card-graph-ql: 100.4.2-beta2
magento/page-builder-commerce: 1.7.3-beta2
magento/product-community-edition: 2.4.6-beta2
magento/security-package-ee: 1.0.1-beta2
magento/theme-adminhtml-spectrum: 100.4.1-beta2
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0, <2.0.1
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
ramsey/uuid: ^4.2
symfony/console: ^5.4
symfony/intl: ^5.4
symfony/process: ^5.4
symfony/string: ^5.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
```

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
      elasticsearch/elasticsearch
    </td>
    <td>库</td>
    <td>用于Elasticsearch的PHP客户端</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
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
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>库</td>
    <td>Adobe Stock API库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>库</td>
    <td>适用于PHP的AWS公共运行时</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>库</td>
    <td>适用于PHP的AWS SDK — 在PHP项目中使用Amazon Web Services</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>隐含</td>
    <td>BraintreeMagento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>库</td>
    <td>LESS处理器的PHP端口</td>
  </tr>
  </tbody>
</table>

### BSD-2 — 子句

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
      <a href="https://github.com/Bacon/BaconQrCode.git">培根/培根 — 二维码</a>
    </td>
    <td>库</td>
    <td>BaconQrCode是PHP的二维码生成器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">贝贝雷/阿瑟特</a>
    </td>
    <td>库</td>
    <td>业务模型中用于输入验证的精简断言库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>库</td>
    <td>PHP 7.1枚举实现</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>库</td>
    <td>安全写入文件的工具，以避免竞争情况</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colimollenhour/cache-backend-file</a>
    </td>
    <td>magento-module</td>
    <td>库存Zend_Cache_Backend_File后端对于标记清除的性能极差，导致其随着缓存项目数的增加而变得不可用。 此后端做出了许多更改，从而极大地提高了性能，尤其是标签清理方面。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colimollenhour/php-redis-session-abstract</a>
    </td>
    <td>库</td>
    <td>具有乐观锁定的基于Redis的会话处理程序</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>库</td>
    <td>reCAPTCHA客户端库，这是一种保护网站抵御垃圾邮件和滥用的免费服务。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">拉米纳斯/拉米纳斯验证码</a>
    </td>
    <td>库</td>
    <td>使用Figlet、图像、ReCaptcha等生成和验证CAPTCHA</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">层叠/层叠 — 编码</a>
    </td>
    <td>库</td>
    <td>PHP Reflection API、静态代码扫描和代码生成的扩展</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">层合板/层合板</a>
    </td>
    <td>库</td>
    <td>提供了基于嵌套对象属性的用户界面，用于访问应用程序代码中的此配置数据</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">层膜/层膜 — 加密</a>
    </td>
    <td>库</td>
    <td>强大的加密工具和密码散列</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>库</td>
    <td>数据库抽象层、SQL抽象、结果集抽象，以及RowDataGateway和TableDataGateway实现</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">拉米纳斯/拉米纳斯 — 迪</a>
    </td>
    <td>库</td>
    <td>PSR-11容器的自动依赖项注入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">拉米纳斯/拉米纳斯逸出者</a>
    </td>
    <td>库</td>
    <td>安全可靠地转义HTML、HTML属性、JavaScript、CSS和URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>库</td>
    <td>触发和侦听PHP应用程序中的事件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">层合板/馈送</a>
    </td>
    <td>库</td>
    <td>提供创建和使用RSS和Atom馈送的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>库</td>
    <td>找到PHP类文件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">层合板/层合板滤镜</a>
    </td>
    <td>库</td>
    <td>以编程方式筛选和标准化数据和文件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">层合板/层合板 — http</a>
    </td>
    <td>库</td>
    <td>提供用于执行超文本传输协议(HTTP)请求的轻松界面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">laminas/laminas-i18n</a>
    </td>
    <td>库</td>
    <td>为您的应用程序提供翻译，并筛选和验证国际化值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>库</td>
    <td>提供了将本机PHP序列化为JSON并将JSON解码为本机PHP的简便方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">层合板/层合板加载器</a>
    </td>
    <td>库</td>
    <td>自动加载和插件加载策略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">层叠/层叠 — 邮件</a>
    </td>
    <td>库</td>
    <td>提供通用功能，用于撰写和发送文本以及MIME兼容的多部分电子邮件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>库</td>
    <td>创建加密安全的伪随机数，并管理大整数</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">层粘连蛋白/层粘连蛋白</a>
    </td>
    <td>库</td>
    <td>创建和解析MIME消息和部分</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">层合板/层合板 — 模块管理器</a>
    </td>
    <td>库</td>
    <td>用于层板MVC应用的模块化应用系统</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>库</td>
    <td>Laminas的事件驱动MVC层，包括MVC应用程序、控制器和插件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">拉米纳斯/拉米纳斯奥auth</a>
    </td>
    <td>库</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>库</td>
    <td>为权限管理提供轻量级和灵活的访问控制列表(ACL)实施</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">拉米纳斯/拉米纳斯 — 雷卡普查</a>
    </td>
    <td>库</td>
    <td>ReCaptcha Web服务的OOP包装器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">层合板/层合板路由器</a>
    </td>
    <td>库</td>
    <td>适用于HTTP和控制台应用程序的灵活路由系统</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>库</td>
    <td>创建基于反射的RPC服务器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>库</td>
    <td>工厂驱动的依赖项注入容器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">层合板/层合板 — 会话</a>
    </td>
    <td>库</td>
    <td>面向PHP会话和存储的面向对象接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">层粘连蛋白/层粘连蛋白</a>
    </td>
    <td>库</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">层粘连蛋白/层粘连蛋白</a>
    </td>
    <td>库</td>
    <td>SPL扩展、数组实用程序、错误处理程序等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">层叠/层叠 — 文本</a>
    </td>
    <td>库</td>
    <td>创建FIGlet和基于文本的表</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>库</td>
    <td>帮助操作和验证“统一资源标识符(URI)”的组件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>库</td>
    <td>适用于各种域的验证类，以及链结验证器以创建复杂验证标准的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">拉米纳斯/拉米纳斯维尤</a>
    </td>
    <td>库</td>
    <td>支持并提供多个视图层、辅助器等的柔性视图层</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>库</td>
    <td>将旧版ZF类名别名更改为Laminas项目等效项。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>库</td>
    <td>用PHP编写的PHP解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>库</td>
    <td>PHP中内置的Javascript微型器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/csmin</a>
    </td>
    <td>库</td>
    <td>YUI CSS压缩器的PHP端口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/twigphp/Twig.git">树枝/树枝</a>
    </td>
    <td>库</td>
    <td>Twig，一种灵活、快速且安全的PHP模板语言</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colimollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>使用Redis的Zend_Cache后端，完全支持标记。</td>
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
      <a href="https://github.com/ezyang/htmlpurifier.git">鄂孜阳/htmlpurifier</a>
    </td>
    <td>库</td>
    <td>使用PHP编写的符合标准的HTML过滤器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>库</td>
    <td>以前称为videlalvaro/php-amqplib。  此库是AMQP协议的纯PHP实现。 它通过RabbitMQ测试。</td>
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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>库</td>
    <td>PHP客户端库Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">积木/数学</a>
    </td>
    <td>库</td>
    <td>任意精度算术库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>库</td>
    <td>var_export()的强大替代方法，它可以在不使用__set_state()的情况下导出关闭项和对象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>库</td>
    <td>根据RFC 4648的Base32编码器/解码器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colimollenhour/credis</a>
    </td>
    <td>库</td>
    <td>Credis是Redis键值存储的轻量级接口，当可用时它会封装phpredis库以提高性能。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>库</td>
    <td>用于查找系统CA捆绑包的路径，并包含对Mozilla CA捆绑包的回退。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">composer/class-map-generator</a>
    </td>
    <td>库</td>
    <td>用于扫描PHP代码和生成类映射的实用程序。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">composer/composer</a>
    </td>
    <td>库</td>
    <td>Composer可帮助您声明、管理和安装PHP项目的依赖项。 它可确保您在所有地方都拥有正确的栈栈。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>库</td>
    <td>处理元数据缩小和扩展的小型实用工具库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">composer/pcre</a>
    </td>
    <td>库</td>
    <td>PCRE包装库，提供类型安全的预浸料_*替换件。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">composer/semver</a>
    </td>
    <td>库</td>
    <td>提供实用程序、版本约束解析和验证的服务器库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>库</td>
    <td>SPDX许可证列表和验证库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>库</td>
    <td>在不使用Xdebug的情况下重新启动进程。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>库</td>
    <td>Endroid QR代码</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>库</td>
    <td>与elasticsearch-php一起使用的guzzle/streams（已放弃）分支</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>库</td>
    <td>与elasticsearch-php一起使用的guzzle/RingPHP（已放弃）分支</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>库</td>
    <td>Guzzle是一个PHP HTTP客户端库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promise</a>
    </td>
    <td>库</td>
    <td>Guzzle promise库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>库</td>
    <td>还提供常用实用程序方法的PSR-7消息实施</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>库</td>
    <td>用于验证json架构的库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">league/flysystem</a>
    </td>
    <td>库</td>
    <td>PHP的文件存储抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>库</td>
    <td>适用于Flysystem的AWS S3文件系统适配器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>库</td>
    <td>用于飞行系统的MIME类型检测</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monolog/monolog</a>
    </td>
    <td>库</td>
    <td>将日志发送到文件、套接字、收件箱、数据库和各种Web服务</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>库</td>
    <td>以声明方式指定如何从JSON文档中提取元素</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>库</td>
    <td>RFC 4648编码的恒定时间实施(Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>库</td>
    <td>PHP 7中的random_bytes()和random_int()的PHP 5.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">佩拉戈/表情符号</a>
    </td>
    <td>库</td>
    <td>将CSS样式转换为HTML代码中的内联样式属性</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>库</td>
    <td>将CSS选择器转换为XPath查询。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>库</td>
    <td>适用于PHP项目的现代DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>库</td>
    <td>用于加密扩展的PHP 5.x-8.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>库</td>
    <td>PHP安全通信库 — RSA、AES、SSH2、SFTP、X.509等的纯PHP实施。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>库</td>
    <td>公共容器接口（PHP图PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>库</td>
    <td>用于事件处理的标准接口。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>库</td>
    <td>HTTP客户端的通用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>库</td>
    <td>PSR-7 HTTP消息工厂的通用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>库</td>
    <td>HTTP消息的通用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>库</td>
    <td>用于记录库的通用界面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>库</td>
    <td>getallheaders的聚合填充。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
    </td>
    <td>库</td>
    <td>用于表示和处理收藏集的PHP库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>库</td>
    <td>用于生成和使用通用唯一标识符(UUID)的PHP库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>库</td>
    <td>适用于PHP的CommonJS Promise/A的轻量级实施</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>库</td>
    <td>以PHP编写的CSS文件的解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>库</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>库</td>
    <td>PHAR文件格式实用程序，用于当PHP向上</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>库</td>
    <td>简单的unix信号处理程序在信号不受支持时静默失败，从而易于进行跨平台开发</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>库</td>
    <td>PHP的AES密钥换行。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>库</td>
    <td>用于根据RFC 4226（HOTP算法）和RFC 6238（TOTP算法）生成一次性密码并与Google Authenticator兼容的PHP库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>库</td>
    <td>用于管理公钥基础结构的PHP框架。 它包括X.509公钥证书、属性证书、证书请求和证书路径验证。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>库</td>
    <td>帮助您查找、加载、组合、自动填写和验证任何类型的配置值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">交响乐/控制台</a>
    </td>
    <td>库</td>
    <td>轻松创建美观且可测试的命令行界面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>库</td>
    <td>将CSS选择器转换为XPath表达式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-injection</a>
    </td>
    <td>库</td>
    <td>允许您标准化并集中处理应用程序中构建对象的方式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">交响曲/弃用合同</a>
    </td>
    <td>库</td>
    <td>用于触发弃用通知的通用函数和约定</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>库</td>
    <td>提供用于管理错误和轻松调试PHP代码的工具</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>库</td>
    <td>提供一些工具，允许应用程序组件通过调度事件并监听事件来相互通信</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher合同</a>
    </td>
    <td>库</td>
    <td>与调度事件相关的一般抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/文件系统</a>
    </td>
    <td>库</td>
    <td>为文件系统提供基本实用程序</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">交响曲/寻找器</a>
    </td>
    <td>库</td>
    <td>通过直观的流畅界面查找文件和目录</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>库</td>
    <td>为HTTP规范定义面向对象层</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>库</td>
    <td>提供将请求转换为响应的结构化流程</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">交响曲/国际号码</a>
    </td>
    <td>库</td>
    <td>为C intl扩展提供一个PHP替换层，其中包括来自ICU库的附加数据</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>库</td>
    <td>用于CTYPE功能的交调聚合填料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>库</td>
    <td>用于intl的grapheme_*函数的Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>库</td>
    <td>用于intl的idn_to_ascii和idn_to_utf8函数的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl — 正规化</a>
    </td>
    <td>库</td>
    <td>Intl的Normalizer类和相关函数的Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>库</td>
    <td>Mbstring扩展的Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 7.2+功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 7.3+功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将某些PHP 8.0及更高功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 8.1+功能回移植到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">交响乐/过程</a>
    </td>
    <td>库</td>
    <td>执行子进程中的命令</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">交响曲/服务合同</a>
    </td>
    <td>库</td>
    <td>与书写服务相关的一般抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>库</td>
    <td>为字符串提供面向对象的API，并以统一的方式处理字节、UTF-8代码点和字形聚类</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>库</td>
    <td>提供用于浏览任何任意PHP变量的机制</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>库</td>
    <td>允许将任何可序列化的PHP数据结构导出为纯PHP代码</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">编码机/保险箱</a>
    </td>
    <td>库</td>
    <td>引发异常而不是出错时返回FALSE的PHP核心函数</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>PHP和Symfony包的JSON对象签名和加密库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>库</td>
    <td>验证方法输入/输出的断言，带有很好的错误消息。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
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
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2模块</td>
    <td>不适用</td>
  </tr>
  <tr>
    <td>
      temando/module-shipping-remover
    </td>
    <td>magento2模块</td>
    <td>从Magento2中删除Temando多承运人运输分机</td>
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
  <tr>
    <td>
      temando/module-shipping
    </td>
    <td>隐含</td>
    <td>适用于Magento2的Temando多承运人运输扩展</td>
  </tr>
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
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
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
    <td>magento2模块</td>
    <td>从Gene Commerce for PayPal的MagentoBraintree2.2.0模块创建分支。</td>
  </tr>
  </tbody>
</table>
