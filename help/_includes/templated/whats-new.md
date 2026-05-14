---
source-git-commit: 726f78414fa49a9d5d2ee4f1b43e718107039530
workflow-type: tm+mt
source-wordcount: '2622'
ht-degree: 0%

---
# 新增功能模板

## 新增功能

本页包含最近60天所做的更改。 我们将从此列表中排除所有次要更新，例如副本编辑。

### 2026年5月13日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>在<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches#valkey-81-lts-support">2.4.5安全修补程序版本</a>、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches#valkey-81-lts-support">2.4.6安全修补程序版本</a>和<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-8-patches#valkey-81-lts-support">2.4.8安全修补程序版本</a>主题中更正了Valkey LTS与8.1的兼容性，以使缓存后端指南与Adobe Commerce上支持的云基础架构上的Valkey相匹配。<br /><em>解决问题<a href="https://github.com/AdobeDocs/commerce-operations.en/issues/177">#177</a>.</em></p>
</td>
      <td>
        技术、反馈、发行说明
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c84f28dc9b90b9206147dffe1eed909d86525345">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了早期Commerce版本的<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">系统要求</a>可折叠部分，其中包含参考表以及针对较旧Adobe Commerce版本的MySQL 8.0 / Elasticsearch 7.17支持终止指南。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/07e7c6904ead0c730597bc6d0899f4c988b7725b">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年5月12日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>在<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions">发布的版本</a>中记录了2026年5月12日的安全修补程序版本和2.4.9 GA。 另外：<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">Adobe Commerce 2.4.7安全修补程序</a>.<br />中更正了2.4.7-p10平台要点(MariaDB 11.8、Valkey 8.1 LTS)- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-8-patches">Adobe Commerce 2.4.8安全修补程序</a>中修复了2.4.8安全修补程序主题描述元数据。</p>
</td>
      <td>
        重大更新，反馈
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c138beddb066fe26f9e57afbd9b6e74f978a8407">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/overview">Overview： Quality Patches Tool (QPT) v1.1.79</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/12093993f31c321afc75da6f2c661b4a9e6fd711">提交</a></td>
    </tr>
    <tr>
      <td><p>更新了v2.4.9的<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/packages/adobe-commerce">包</a>、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises">bin/magento</a>和<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings#verify-installed-extensions">必需的PHP扩展</a>。<br />更新了安全修补程序发行说明(2.4.4、2.4.5、2.4.6、2.4.7、2.4.8)，以引用<a href="https://helpx.adobe.com/security/products/magento/apsb26-49.html">Adobe安全公告APSB26-49</a>并记录<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-8-patches">2.4.8修补程序</a>、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7修补程序</a>、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6的新平台兼容性亮点修补程序</a>、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5修补程序</a>和<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-4-patches">2.4.4修补程序</a>。<br />已更新<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">Adobe Commerce 2.4.9发行说明</a>和<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-9">Magento Open Source 2.4.9发行说明</a>，其中包含GA修复的问题数据并包含与2.4.9版本一致的路径（取代Beta版的修复问题源）。<br />已更新<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">Adobe Commerce 2.4.9发行说明</a>和<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-9">Magento Open Source 2.4.9发行说明</a>（适用于GA）的重点部分。<br />已更新<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">系统要求</a>（适用于2.4.9）、最近的安全修补程序行、以及内部部署和云依赖关系表。<br />已将<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/uct">UCT CLI引用</a>更新为版本3.0.27。<br />已更新有关Commerce 2.4.9 Symfony缓存支持的缓存配置文档：<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/redis-pg-cache">对默认缓存使用Redis</a> — 已添加用于性能优化的Zend和Symfony缓存实施的选项卡式内容。<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/valkey/valkey-pg-cache">对默认缓存使用Valkey</a> — 已添加用于性能优化的Zend和Symfony缓存实施的选项卡式内容。<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/level-two-cache">L2缓存</a> — 已添加现代式symfony L2缓存实现（<code class="language-plaintext highlighter-rouge">symfony_l2</code>后端）支持过时的缓存。<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/cache-options">缓存选项</a> — 添加了比较基于Zend的缓存后端和Symfony缓存后端的实现选项。<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/cache-types">缓存类型</a> — 添加了对新式Symfony缓存后端类型的引用。</p>
</td>
      <td>
        重大更新
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/baa2cd68fe266f6f31113ff1adba4342e6f427ef">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年5月11日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4628">ACP2E-4628的QPT 1.1.78修复的详细说明：当“帐户共享”设置为“全局</a>”时，导入具有大写电子邮件地址的客户会触发未定义的数组键错误。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c2c4f04d05b5bd1b60936256d3dbd6be5f396c5b">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4763">ACP2E-4763的QPT 1.1.78修复的详细说明： GraphQL customerOrders查询返回夸大的original_price_include_tax和original_row_total_include_tax</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6f156475e60ca0f8ac365306e282c90156837567">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acsd-60989">ACSD-60989的QPT 1.1.78修复的详细说明：通过声明性架构修改带有外键的列会在MariaDB</a>上导致错误。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/9001c0e440f8a80e618bcf68a72cb6ac1533a2c0">提交</a></td>
    </tr>
    <tr>
      <td><p>更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility">共享责任安全和操作模型</a>，以明确商家必须在主动支持的版本上保留Platform Services、第三方依赖项和Commerce Services扩展，以使其符合Adobe安全支持的条件，并针对PHP、MariaDB、Redis和OpenSearch制定了新指南。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/4b841ca5a55640e770fdbec71869fad6d6564fe8">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年5月7日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4732">ACP2E-4732的QPT 1.1.78修复的详细说明：当changelog表中的version_id列达到其最大值</a>时，将停止对具有许多更新的客户进行部分索引。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/063a15996a683a90770b699b413fb25dd7489035">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4591">ACP2E-4591的QPT 1.1.78修复程序的详细说明：基于订单计数的客户区段（如“首次购买者”）在通过REST API</a>下订单时不会更新。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/53cdfe439238edc2148004efab3300653e891765">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年5月6日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4456">ACP2E-4456的QPT 1.1.78修复的详细说明：取消带有GraphQL突变的订单不会将完全使用礼品卡支付的订单移至“已关闭”状态</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/570b9f8230384387166412ddd418f8130e2853bd">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年5月4日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4448">ACP2E-4448的QPT 1.1.78修复的详细说明： [!DNL Redis]中断期间所做的配置更改在[!DNL Redis]恢复后不会反映出来，并且过时的值会保留</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/fd467c92e3fa56db4a606118afe571ed932185fd">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4452">ACP2E-4452的QPT 1.1.78修复程序的详细说明：“快速订单”页面上的产品价格包含税，而不考虑税显示配置</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/cf3a631a71997d54cd28de9afecaae0769d602b6">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年5月1日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4665">ACP2E-4665的QPT 1.1.78修复的详细说明：通过REST API</a>请求时，产品库中带有视频的可配置产品的子产品不会显示。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/8753c098963a0b2df6a4135e9a8038211bbb93d1">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月30日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4613">ACP2E-4613的QPT 1.1.78修复的详细说明：大型媒体目录结构缓慢的gettree响应和延迟媒体集目录树加载</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ae0f38980186b40f4ffd6d81bbe2104f3e8238fc">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月29日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4535">ACP2E-4535的QPT 1.1.78修复的详细说明：提交忘记密码表单会破坏或重新生成会话（PHPSESSID更改）并清除来宾购物车</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/953e231d2161d84e2444fa46ac95b93dbba28241">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4507">ACP2E-4507的QPT 1.1.78修复的详细说明：“密码选项”配置不适用于通过GraphQL变动</a>发出的客户密码重置请求。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b657f2e50d48c9179d1c6b3559ee7e6ee99b306d">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4609">ACP2E-4609的QPT 1.1.78修复程序的详细说明：当某些引号包含已删除的产品</a>时，“我的引号”页面不显示任何引号。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/670dacfa2bdc211eb9f4ed6788144ba6c1dac678">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4431">ACP2E-4431的QPT 1.1.78修复的详细说明：在重新索引进程</a>期间已删除与目标规则匹配的相关产品。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/f9424da66669c54eb0a794555ea7df66625f6c71">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4416">ACP2E-4416的QPT 1.1.78修复程序的详细说明：在Admin</a>中创建客户奖励点时不会初始化。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/517b6c299474497378966a4a2122a6854f3f7be1">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月28日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4540">ACP2E-4540的QPT 1.1.78修复的详细说明： Fotorama库未正确加载，因此只有第一个附加的图像可见</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/bfab19dc07ecc1c314c530d053b82e3408478c41">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月27日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522">ACP2E-4522的QPT 1.1.78修复的详细说明：当同时运行多个购物车合并或报价保存请求时，quote_coupons表上会发生间歇性的重复键错误</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/13abccbeb79cdb3377dcea9528ffcb13b491a8d8">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565">ACP2E-4565的QPT 1.1.78修复程序的详细说明：使用X-Adobe-Company标头时，GraphQL公司查询返回“当前客户未获得授权”</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/0ee08b94a3b56febff5d2126af71d2b964846f7a">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419">ACP2E-4419的QPT 1.1.78修复的详细说明：在店面</a>上成功进行reCAPTCHA v2验证后，礼品卡在结账时无法正确应用。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/7c7052efdd8b10be705959c854064eaed484d796">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555">ACP2E-4555的QPT 1.1.78修复程序的详细说明：包含句点或正斜杠的电话号码无法正确验证</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ee63f4566c476877588dde5ff002ac105f2e4764">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月23日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/overview">Overview： Quality Patches Tool (QPT) v1.1.78</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3f14416d89140ee75ec437a42fbebae804282b72">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月20日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><ul>
  <li>更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy">生命周期策略</a>，修订了终止支持表、扩展的支持范围以及有关2.4.4和2.4.5的其他安全修补程序设置的新部分。<br /> — 更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/versioning-policy">版本策略</a>和<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule">版本计划</a>，内容涉及隔离的安全修补程序先决条件和修补程序/通过质量修补程序工具进行的单独修补程序交付；将隔离的安全修补程序详细信息移入共享安全修补程序概述中。<br /> — 更新了2026版日历以符合当前计划。</li>
</ul>
</td>
      <td>
        技术、重大更新
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/0bc6807d7f4bfd84ac698de81f8cf6f56d849af7">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月8日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>更新了New Relic (APM)支持的Commerce on Cloud版本的<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">系统要求</a>。</p>
</td>
      <td>
        技术，反馈
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/f82d05cf0f7d2749b313ef5f7e89e1e36248bf30">提交</a></td>
    </tr>
    <tr>
      <td><p>更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/beta">Beta版本</a>，其中包含SaaS项目的类别促销（公共Beta）计划，包括指向<a href="https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add">类别促销</a>和相关促销规则主题的链接。</p>
</td>
      <td>
        重大更新
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a9f3594a0ccf4326b0541a4f2b07fdf49cde7148">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月3日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了正确覆盖<code class="language-plaintext highlighter-rouge">env.php</code>中Adobe Commerce的默认L2缓存目录的说明，以确保缓存文件存储在预期的位置，并防止拆分缓存目录和GlusterFS分段错误。 请参阅<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-service-configuration">Redis和Valkey服务配置</a>的最佳实践中的更新指南。</p>
</td>
      <td>
        技术，反馈
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c3030226d7832b17c82be375431795cba44d72f9">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月1日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>已使用最新发行信息更新<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule">2026 Adobe Commerce发行日历</a>。</p>
</td>
      <td>
        发行说明
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3f32d342cbdc3e962fede45de828d836c242bc9a">提交</a></td>
    </tr>
    <tr>
      <td><p>更新了Redis和Valkey配置的<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">最佳实践</a>并提供相关配置指导。</p>
</td>
      <td>
        技术，反馈
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c96e5b397a2ffee8fadaf638e721799b40d320d3">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月19日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319">ACSD-69319的QPT 1.1.76修复的详细说明：当子产品在自定义源</a>下有库存时，捆绑价格未正确索引。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/7646d46e37385cf0a2bfbee6de82410ca54629a1">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月18日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086">ACSD-69086的QPT 1.1.76修复的详细说明：由于不支持的数据库版本检查</a>，在MariaDB 10.11上安装失败。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/016d24d990492d009677c218b253ae88c21634e6">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月17日

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>描述</th>
      <th>类型</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331">ACSD-69331的QPT 1.1.76修复程序的详细说明：媒体集中的内容创建者无法创建仅具有<code class="language-plaintext highlighter-rouge">create_folder</code>权限的文件夹。 修复后，他们可以按预期创建文件夹</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/40a14de0a67a0c373dcbb497f1893a98322435b3">提交</a></td>
    </tr>
  </tbody>
</table>
