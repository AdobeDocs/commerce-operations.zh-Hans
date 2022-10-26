---
source-git-commit: a3fa25993f365a85307db45ef16f68eeb12604bb
workflow-type: tm+mt
source-wordcount: '2193'
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

的 `composer.json` 文件声明了包列表，而 `composer.lock` 文件存储用于构建Adobe Commerce或Magento Open Source安装的软件包的完整列表（每个软件包及其依赖项的完整版本）。

以下参考文档是从 `composer.lock` 文件，且其中包含Adobe Commerce 2.4.5中包含的必需包。

## 依赖关系

`magento/product-enterprise-edition 2.4.5` 具有以下依赖项：

```config
colinmollenhour/cache-backend-file: ~1.4.1
colinmollenhour/cache-backend-redis: 1.14.2
colinmollenhour/credis: 1.13.0
colinmollenhour/php-redis-session-abstract: ~1.4.5
composer/composer: ^1.9 || ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0
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
guzzlehttp/guzzle: ^7.4.2
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ~4.5.0
laminas/laminas-db: ^2.15.0
laminas/laminas-dependency-plugin: ^2.2.0
laminas/laminas-di: ^3.7.0
laminas/laminas-escaper: ~2.10.0
laminas/laminas-eventmanager: ^3.5.0
laminas/laminas-feed: ^2.17.0
laminas/laminas-http: ^2.15.0
laminas/laminas-json: ^3.3.0
laminas/laminas-mail: ^2.16.0
laminas/laminas-mime: ^2.9.1
laminas/laminas-modulemanager: ^2.11.0
laminas/laminas-mvc: ^3.3.3
laminas/laminas-server: ^2.11.1
laminas/laminas-servicemanager: ^3.11.0
laminas/laminas-soap: ^2.10.0
laminas/laminas-stdlib: ^3.7.1
laminas/laminas-uri: ^2.9.1
laminas/laminas-validator: ^2.17.0
league/flysystem: ~2.4.5
league/flysystem-aws-s3-v3: ^2.4.3
lib-libxml: *
magento/composer: ~1.8.0
magento/composer-dependency-version-audit-plugin: ~0.1
magento/framework-foreign-key: 100.4.4
magento/magento-composer-installer: >=0.3.0
magento/magento2-ee-base: 2.4.5
magento/module-admin-gws: 100.4.5
magento/module-admin-gws-configurable-product: 100.4.2
magento/module-admin-gws-staging: 100.4.2
magento/module-advanced-catalog: 100.4.2
magento/module-advanced-checkout: 100.4.5
magento/module-advanced-rule: 100.4.2
magento/module-advanced-sales-rule: 100.4.2
magento/module-async-order: 100.4.1
magento/module-async-order-graph-ql: 100.4.0
magento/module-aws-s3-customer-custom-attributes: 100.4.2
magento/module-aws-s3-gift-card-import-export: 100.4.2
magento/module-aws-s3-scheduled-import-export: 100.4.2
magento/module-banner: 101.2.5
magento/module-banner-customer-segment: 100.4.3
magento/module-banner-graph-ql: 100.4.1
magento/module-bundle-import-export-staging: 100.4.2
magento/module-bundle-staging: 100.4.5
magento/module-catalog-event: 101.1.4
magento/module-catalog-import-export-staging: 100.4.2
magento/module-catalog-inventory-staging: 100.4.3
magento/module-catalog-permissions: 100.4.5
magento/module-catalog-permissions-graph-ql: 100.4.3
magento/module-catalog-rule-staging: 100.4.5
magento/module-catalog-staging: 100.4.5
magento/module-catalog-staging-graph-ql: 100.4.4
magento/module-catalog-url-rewrite-staging: 100.4.4
magento/module-checkout-address-search: 100.4.4
magento/module-checkout-address-search-gift-registry: 100.4.1
magento/module-checkout-staging: 100.4.4
magento/module-cms-staging: 100.4.5
magento/module-configurable-product-staging: 100.4.4
magento/module-custom-attribute-management: 100.4.4
magento/module-customer-balance: 100.4.5
magento/module-customer-balance-graph-ql: 100.4.2
magento/module-customer-custom-attributes: 100.4.5
magento/module-customer-finance: 100.4.2
magento/module-customer-segment: 102.1.5
magento/module-deferred-total-calculating: 100.4.0
magento/module-downloadable-staging: 100.4.4
magento/module-elasticsearch-catalog-permissions: 100.4.1
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.0
magento/module-enterprise: 100.4.3
magento/module-gift-card: 101.3.5
magento/module-gift-card-account: 101.2.5
magento/module-gift-card-account-graph-ql: 100.4.3
magento/module-gift-card-graph-ql: 100.4.5
magento/module-gift-card-import-export: 100.4.2
magento/module-gift-card-staging: 100.4.2
magento/module-gift-message-staging: 100.4.2
magento/module-gift-registry: 101.2.5
magento/module-gift-registry-graph-ql: 100.4.1
magento/module-gift-wrapping: 101.2.4
magento/module-gift-wrapping-graph-ql: 100.4.2
magento/module-gift-wrapping-staging: 100.4.2
magento/module-google-optimizer-staging: 100.4.2
magento/module-google-tag-manager: 100.4.5
magento/module-grouped-product-staging: 100.4.3
magento/module-invitation: 100.4.4
magento/module-layered-navigation-staging: 100.4.2
magento/module-logging: 101.2.5
magento/module-login-as-customer-logging: 100.4.5
magento/module-login-as-customer-website-restriction: 100.4.3
magento/module-media-content-catalog-staging: 100.4.2
magento/module-msrp-staging: 100.4.3
magento/module-multiple-wishlist: 100.4.5
magento/module-multiple-wishlist-graph-ql: 100.4.1
magento/module-payment-staging: 100.4.2
magento/module-persistent-history: 100.4.2
magento/module-price-permissions: 100.4.1
magento/module-product-video-staging: 100.4.2
magento/module-promotion-permissions: 100.4.2
magento/module-quote-gift-card-options: 100.4.2
magento/module-quote-staging: 100.4.2
magento/module-reminder: 101.2.4
magento/module-remote-storage-commerce: 100.4.1
magento/module-resource-connections: 100.4.2
magento/module-review-staging: 100.4.2
magento/module-reward: 101.2.5
magento/module-reward-graph-ql: 100.4.4
magento/module-reward-staging: 100.4.2
magento/module-rma: 101.2.5
magento/module-rma-graph-ql: 100.4.4
magento/module-rma-staging: 100.4.2
magento/module-sales-archive: 101.0.3
magento/module-sales-rule-staging: 100.4.4
magento/module-scalable-checkout: 100.4.4
magento/module-scalable-inventory: 100.4.3
magento/module-scalable-oms: 100.4.3
magento/module-scheduled-import-export: 101.2.5
magento/module-search-staging: 100.4.3
magento/module-staging: 101.2.5
magento/module-staging-graph-ql: 100.4.2
magento/module-support: 101.2.4
magento/module-swat: 100.4.3
magento/module-target-rule: 101.2.5
magento/module-target-rule-graph-ql: 100.4.2
magento/module-versions-cms: 101.2.5
magento/module-versions-cms-page-cache: 100.4.1
magento/module-versions-cms-url-rewrite: 100.4.3
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.1
magento/module-visual-merchandiser: 100.4.5
magento/module-website-restriction: 100.4.4
magento/module-weee-staging: 100.4.2
magento/module-wishlist-gift-card: 100.4.1
magento/module-wishlist-gift-card-graph-ql: 100.4.1
magento/page-builder-commerce: 1.7.2
magento/product-community-edition: 2.4.5
magento/security-package-ee: 1.0.0
magento/theme-adminhtml-spectrum: 100.4.0
magento/zendframework1: ~1.15.0
monolog/monolog: ^2.7
pelago/emogrifier: ^6.0.0
php: ~7.4.0||~8.1.0
php-amqplib/php-amqplib: ~3.2.0
phpseclib/mcrypt_compat: ~2.0.2
phpseclib/phpseclib: ~3.0.13
ramsey/uuid: ~4.2.0
symfony/console: ~4.4.0
symfony/process: ~4.4.0
tedivm/jshrink: ~1.4.0
tubalmartin/cssmin: 4.1.1
web-token/jwt-framework: ^v2.2.7
webonyx/graphql-php: ~14.11.6
wikimedia/less.php: ^3.0.0
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
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>库</td>
    <td>用于Elasticsearch的PHP客户端</td>
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
    <td>AWS PHP的常用运行时</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>库</td>
    <td>AWS SDK for PHP — 在PHP项目中使用Amazon Web Services</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>元包</td>
    <td>BraintreeMagento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>库</td>
    <td>Javascript版本LESS http://lesscss.org的PHP端口（最初由Josh Schmidt维护）</td>
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
      <a href="https://github.com/Bacon/BaconQrCode.git">培根/培根 — qr码</a>
    </td>
    <td>库</td>
    <td>BaconQrCode是用于PHP的QR代码生成器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">贝贝雷/阿塞特</a>
    </td>
    <td>库</td>
    <td>用于业务模型中输入验证的精简断言库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>库</td>
    <td>PHP 7.1枚举实施</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe writer</a>
    </td>
    <td>库</td>
    <td>安全写入文件的工具，以避免争用情况</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento-module</td>
    <td>库Zend_Cache_Backend_File后端的标记清除性能极差，因此当缓存项目数量增加时，库将变得不可用。 此后端会进行许多更改，从而极大地提升了性能，特别是对于标记清理而言。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>使用Redis的Zend_Cache后端完全支持标记。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>库</td>
    <td>具有乐观锁定的基于Redis的会话处理程序</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>库</td>
    <td>reCAPTCHA的客户端库，这是一种免费服务，可保护网站免受垃圾邮件和滥用。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-capcha</a>
    </td>
    <td>库</td>
    <td>使用图像、图像、ReCaptcha等生成和验证CAPTCHA</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">层粘连码</a>
    </td>
    <td>库</td>
    <td>对PHP反射API、静态代码扫描和代码生成的扩展</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas配置</a>
    </td>
    <td>库</td>
    <td>提供基于嵌套对象属性的用户界面，用于在应用程序代码中访问此配置数据</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>库</td>
    <td>数据库抽象层、SQL抽象、结果集抽象、RowDataGateway和TableDataGateway实现</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-dependency-plugin.git">laminas/laminas-dependency-plugin</a>
    </td>
    <td>composer-plugin</td>
    <td>将zendframework和zfcampus包替换为其Laminas项目等效项。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">拉米纳/拉米纳</a>
    </td>
    <td>库</td>
    <td>PSR-11容器的自动依赖项注入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">层带/层带式擒纵机</a>
    </td>
    <td>库</td>
    <td>安全、安全地转义HTML、HTML属性、JavaScript、CSS和URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>库</td>
    <td>触发和侦听PHP应用程序内的事件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">层粘连蛋白/层粘连蛋白饲料</a>
    </td>
    <td>库</td>
    <td>提供用于创建和使用RSS和Atom源的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas.http</a>
    </td>
    <td>库</td>
    <td>为执行超文本传输协议(HTTP)请求提供简单的接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas.json</a>
    </td>
    <td>库</td>
    <td>为将本机PHP序列化为JSON和将JSON解码为本机PHP提供了方便的方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">层板/层板装载机</a>
    </td>
    <td>库</td>
    <td>自动加载和插件加载策略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas mail</a>
    </td>
    <td>库</td>
    <td>提供编写和发送文本与MIME兼容的多部分电子邮件的通用功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>库</td>
    <td>创建和解析MIME消息和部分</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">层叠/层叠模块管理器</a>
    </td>
    <td>库</td>
    <td>用于laminas-mvc应用的模块化应用系统</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas/mvc</a>
    </td>
    <td>库</td>
    <td>Laminas的事件驱动MVC层，包括MVC应用程序、控制器和插件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas/recaptcha</a>
    </td>
    <td>库</td>
    <td>ReCaptcha Web服务的OOP包装器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas路由器</a>
    </td>
    <td>库</td>
    <td>用于HTTP和控制台应用程序的灵活路由系统</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas服务器</a>
    </td>
    <td>库</td>
    <td>创建基于反射的RPC服务器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas服务管理器</a>
    </td>
    <td>库</td>
    <td>工厂驱动的依赖性注入容器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas会话</a>
    </td>
    <td>库</td>
    <td>PHP会话和存储的面向对象接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">层粘连蛋白/层粘连蛋白皂</a>
    </td>
    <td>库</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>库</td>
    <td>SPL扩展、阵列实用程序、错误处理程序等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">层叠图/层叠图文本</a>
    </td>
    <td>库</td>
    <td>创建图表和基于文本的表</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>库</td>
    <td>有助于处理和验证统一资源标识符(URI)的组件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">层粘连/层粘连验证器</a>
    </td>
    <td>库</td>
    <td>适用于各种域的验证类，以及链式验证器创建复杂验证标准的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">层叠图/层叠图</a>
    </td>
    <td>库</td>
    <td>灵活的视图层支持并提供多视图层、帮助器等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>库</td>
    <td>Laminas Project的别名旧版ZF类名称。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php解析器</a>
    </td>
    <td>库</td>
    <td>用PHP编写的PHP解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>库</td>
    <td>在PHP中内置的Javascript缩小程序</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">图巴马丁/克斯明</a>
    </td>
    <td>库</td>
    <td>YUI CSS压缩程序的PHP端口</td>
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
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlputer</a>
    </td>
    <td>库</td>
    <td>使用PHP编写的符合标准的HTML过滤器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-ampqplib</a>
    </td>
    <td>库</td>
    <td>以前称为videolalvaro/php-ampqplib。  此库是AMQP协议的纯PHP实现。 它已经用RabbitMQ测试了。</td>
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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree/php</a>
    </td>
    <td>库</td>
    <td>BraintreePHP客户端库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">brick/math</a>
    </td>
    <td>库</td>
    <td>任意精度算术库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>库</td>
    <td>var_export()的强大替代方法，它可以导出闭包和对象，而不__set_state()</td>
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
      <a href="https://github.com/colinmollenhour/credis.git">科林莫伦霍尔/克雷德</a>
    </td>
    <td>库</td>
    <td>Credis是Redis键值存储的轻量级界面，在提供phpredis库以提高性能时，该界面会封装phpredis库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>库</td>
    <td>允许您找到系统CA包的路径，并包含回退到Mozilla CA包。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">编辑器/编辑器</a>
    </td>
    <td>库</td>
    <td>编辑器可帮助您声明、管理和安装PHP项目的依赖项。 它可确保您在任何位置都拥有正确的堆栈。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>库</td>
    <td>可处理元数据缩小和扩展的小型实用程序库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">编辑器/pcre</a>
    </td>
    <td>库</td>
    <td>提供类型安全预置_*替换的PCRE包装库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">composer/semver</a>
    </td>
    <td>库</td>
    <td>提供实用工具、版本约束解析和验证的组件库。</td>
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
      <a href="https://github.com/endroid/qr-code.git">android/qr代码</a>
    </td>
    <td>库</td>
    <td>Endroid QR代码</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">齐穆埃尔/古兹莱斯特雷姆</a>
    </td>
    <td>库</td>
    <td>要与elasticsearch-php一起使用的Guzzle/流分支（已放弃）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>库</td>
    <td>将与elasticsearch-php一起使用的guzzle/RingPHP（已放弃）分支</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/fgrosse/PHPASN1.git">fgrosse/phpasn1</a>
    </td>
    <td>库</td>
    <td>一种PHP框架，它允许您使用ITU-T X.690编码规则对任意ASN.1结构进行编码和解码。</td>
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
      <a href="https://github.com/guzzle/promises.git">guzzlettp/promises</a>
    </td>
    <td>库</td>
    <td>Guzzle承诺库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>库</td>
    <td>PSR-7消息实施，该消息实施还提供常用实用工具方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json模式</a>
    </td>
    <td>库</td>
    <td>用于验证JSON架构的库。</td>
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
    <td>AWS Flysystem的S3文件系统适配器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime类型检测</a>
    </td>
    <td>库</td>
    <td>Flysystem的MIME类型检测</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">单对数/单对数</a>
    </td>
    <td>库</td>
    <td>将日志发送到文件、套接字、收件箱、数据库和各种Web服务</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>库</td>
    <td>声明性地指定如何从JSON文档提取元素</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>库</td>
    <td>RFC 4648编码的恒时实现(Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>库</td>
    <td>PHP 7中随机字节()和随机整数()的PHP 5.x多填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">亚速尔群岛语</a>
    </td>
    <td>库</td>
    <td>在HTML代码中将CSS样式转换为内联样式属性</td>
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
    <td>用于PHP项目的现代DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>库</td>
    <td>用于MCRYPT扩展的PHP 5.x-8.x聚填充</td>
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
      <a href="https://github.com/php-fig/container.git">psr/容器</a>
    </td>
    <td>库</td>
    <td>通用容器接口（PHP图PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>库</td>
    <td>用于事件处理的标准界面。</td>
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
    <td>PSR-7 HTTP报文工厂的常见接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>库</td>
    <td>HTTP消息的常用接口</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>库</td>
    <td>记录库的常用界面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getalheaders</a>
    </td>
    <td>库</td>
    <td>用于几何标题的多填充。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">拉姆齐/收藏集</a>
    </td>
    <td>库</td>
    <td>用于表示和处理集合的PHP库。</td>
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
    <td>对PHP的CommonJS Promise/A进行轻量级实施</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>库</td>
    <td>用PHP编写的CSS文件解析器</td>
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
    <td>PHAR文件格式实用程序，当PHP将您升级时</td>
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
      <a href="https://github.com/Spomky-Labs/base64url.git">spomky-labs/base64url</a>
    </td>
    <td>库</td>
    <td>基本64 URL安全编码/解码PHP库</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>库</td>
    <td>一种PHP库，用于根据RFC 4226（HOTP算法）和RFC 6238（TOTP算法）生成一次性密码，并与Google Authenticator兼容</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>库</td>
    <td>帮助您查找、加载、组合、自动填充和验证任何类型的配置值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
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
      <a href="https://github.com/symfony/debug.git">symony/debug</a>
    </td>
    <td>库</td>
    <td>提供轻松调试PHP代码的工具</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency/incleption</a>
    </td>
    <td>库</td>
    <td>允许您标准化和集中化应用程序中构建对象的方式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contracts</a>
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
    <td>提供工具，允许应用程序组件通过调度事件并侦听事件来彼此通信</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contracts</a>
    </td>
    <td>库</td>
    <td>与调度事件相关的一般抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symony/filesystem</a>
    </td>
    <td>库</td>
    <td>为文件系统提供基本实用工具</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symony/finder</a>
    </td>
    <td>库</td>
    <td>通过直观的fluent界面查找文件和目录</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-contracts</a>
    </td>
    <td>库</td>
    <td>与HTTP客户端相关的通用抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http/foundation</a>
    </td>
    <td>库</td>
    <td>为HTTP规范定义面向对象的层</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http/kernel</a>
    </td>
    <td>库</td>
    <td>提供将请求转换为响应的结构化流程</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill/ctype</a>
    </td>
    <td>库</td>
    <td>类型函数的符号多填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>库</td>
    <td>对国际号码的idn_to_ascii和idn_to_utf8函数的符号多填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>库</td>
    <td>Intl标准化子类的符号多填充及其相关函数</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>库</td>
    <td>Mbstring扩展的符号多填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 7.2+功能回填到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 7.3+功能回填到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 8.0及更高版本的功能回填到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>库</td>
    <td>Symfony polyfill将一些PHP 8.1+功能回填到较低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symony/process</a>
    </td>
    <td>库</td>
    <td>在子进程中执行命令</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-contracts</a>
    </td>
    <td>库</td>
    <td>与编写服务相关的通用抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>库</td>
    <td>提供用于遍历任意PHP变量的机制</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">防毒机/安全箱</a>
    </td>
    <td>库</td>
    <td>PHP核心函数，该函数引发异常，而不是在出错时返回FALSE</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>用于PHP和Symfony包的JSON对象签名和加密库。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>库</td>
    <td>使用好错误消息验证方法输入/输出的断言。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>库</td>
    <td>GraphQL引用实现的PHP端口</td>
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
    <td>magento2-module</td>
    <td>不适用</td>
  </tr>
  <tr>
    <td>
      temando/module-shipping-remover
    </td>
    <td>magento2-module</td>
    <td>从Magento2中删除Temando多运营商送货扩展</td>
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
    <td>元包</td>
    <td>适用于Magento2的Temando多运营商送货扩展</td>
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
      <a href="https://github.com/2tvenom/CBOREncode.git">2crepule/cborencode</a>
    </td>
    <td>库</td>
    <td>用于PHP的CBOR编码器</td>
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
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>magento2-module</td>
    <td>从MagentoBraintree2.2.0模块中创建分支，由Gene Commerce for PayPal提供。</td>
  </tr>
  </tbody>
</table>
