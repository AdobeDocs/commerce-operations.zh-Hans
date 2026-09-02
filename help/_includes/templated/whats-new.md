---
source-git-commit: 3d85f2181ca7d234ceb181583533b25884b12fe1
workflow-type: tm+mt
source-wordcount: '2047'
ht-degree: 1%

---
# 新增功能模板

## 新增功能

本页包含最近60天所做的更改。 我们将从此列表中排除所有次要更新，例如副本编辑。

### 2026年8月26日

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
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4840">ACP2E-4840的QPT 1.1.82修复的详细说明： GraphQL产品查询为自定义库存库存上的库存产品返回空数量</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/edfc38af34925749c5acb36d2c0bcfc5d16a577a">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月19日

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
      <td><p>更新了Commerce缓存文档，更新了本地与Cloud指南以及迁移到Valkey with Symfony L2缓存的新迁移指南：<br /> — 更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/caching-overview">缓存概述和配置选项</a>。<br /> — 更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/cache-types">配置缓存前端和类型</a>。<br /> — 更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/cache-options">缓存后端选项和存储引用</a>。<br /> — 更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/level-two-cache">L2缓存配置以进行性能优化</a>，并提供了从<code>RemoteSynchronizedCache</code>迁移到Symfony L2缓存的指南。<br /> — 更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">最佳实践Valkey和Redis服务配置</a>，带有云特定的迁移步骤，可迁移到Valkey和Symfony L2缓存。</p>
</td>
      <td>
        重大更新
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3a840b544de95a4bb17ef49d0325b16d461aecaa">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月14日

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
      <td><p>更新了客户如何在Cloud UI中检查其服务依赖项版本的步骤，并更新了指南的链接，该指南介绍了客户如何在<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/security-enforcement-policy#action-1-verify-and-upgrade-third-party-software-dependencies">验证和升级第三方软件依赖项</a>中为他们的存储生成升级兼容性报告。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/54ac98c35e1f161f390587601484db4e3294b6af">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月13日

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
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4194">ACP2E-4194的QPT 1.1.82修复的详细说明：具有未知筛选器名称的GraphQL请求会导致PHP异常日志</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d4202395c5b7bb5e8c4a95d8fb353ec0fc523fcb">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4695">ACP2E-4695的QPT 1.1.82修复的详细说明：由于内存使用量过高而导致目录规则索引器内存不足故障</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/dc891435d573c4c333e58e25b2dbe003ffa08f27">提交</a></td>
    </tr>
    <tr>
      <td><p>修复了Adobe Commerce 2.4.5和2.4.6版本的EOS日期中的拼写错误。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/8de65d309dcd4158627910ce5c0b87966db5c948">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月12日

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
      <td><p>已将PHP 8.4作为<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9#php-and-composer">2.4.9发行说明</a>中支持的PHP版本删除，因为不建议将其用于生产环境，并且仅用于升级兼容性。</p>
</td>
      <td>
        发行说明，技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/603bb70012a2f92ceeaad644d5252c4677a1a47c">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4894">ACP2E-4894的QPT 1.1.82修复程序的详细说明：启用异步索引时，“管理订单”网格中会显示新订单，并且存在延迟</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ad40d94c1618f7e423fd6a773185b8fba48c2c72">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4698">ACP2E-4698的QPT 1.1.82修复的详细说明：页面生成器文本内联编辑保存了绝对媒体URL，而不是可移植指令</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/68e5e99ac0717b0e358acd6acf9934044a917a82">提交</a></td>
    </tr>
    <tr>
      <td><p>更正并完成<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions">已发布版本</a>页面上多个Adobe Commerce发行行的支持终止、扩展支持和其他安全修复配置日期。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/fc5a7f7a466e6419a3e712bcbec4224f98f8c480">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月11日

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
      <td><p>更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">系统要求</a>以将RabbitMQ 3.13添加为Adobe Commerce 2.4.4-p18（最新）的支持版本，从而解决Debian OS升级路径的阻止程序。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/046d641dc45b269c6495bef0c06c53bdc500227b">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月10日

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
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797">ACP2E-4797的QPT 1.1.82修复程序的详细说明：当支持utf8mb4时，管理员WYSIWYG编辑器和页面生成器会阻止4字节的Unicode字符</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c97bb9c77eb0ec4bbc92d042cfa9fd440e970ca7">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了针对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682">ACP2E-4682的QPT 1.1.82修复的详细说明：检查报价为isActive的店面页面创建空报价记录</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ceac870e3ccb9eeee64e3b574aaccd33c6ab69d0">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799">ACP2E-4799的QPT 1.1.82修复的详细说明： GraphQL查询requisition_lists返回错误的total_count，分页</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/19f854db1a0ff78d0a6dca070b4b6db09d3de83e">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870">ACP2E-4870的QPT 1.1.82修复的详细说明：产品警报电子邮件忽略商店视图电子邮件设置</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/907df07e641ab7124353f89ca799f92d097aa54f">提交</a></td>
    </tr>
    <tr>
      <td><p>更新了支持Adobe Commerce 2.4.9的<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability">产品可用性</a>表，并删除了Page Builder条目，该条目自2.4.3以来一直是核心产品的一部分。</p>
</td>
      <td>
        重大更新
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a5120adab9f624677447889722359951e775c3f3">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月9日

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
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593">ACP2E-4593的QPT 1.1.82修复程序的详细说明：在多网站店面</a>的辅助网站上提供了错误的网站限制CMS页面。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/86c85db0098192092241b680d38b882f1a52b578">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月6日

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
      <td><p>更正了Adobe Commerce 2.4.6、2.4.7和2.4.8的<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability">产品可用性</a>中的B2B扩展版本支持列表。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/50fb71aa968abf1302e86ffeb3d3b3a66b3c33d5">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月31日

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
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547">ACP2E-4547的QPT 1.1.82修复的详细说明：如果未将默认目录产品分配给用户的共享目录</a>，则管理员无法将它添加到报价中。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6d0313c01e979d3d4bd3e781e2f0e9c336bbd8c5">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月30日

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
      <td><p>为Adobe Commerce on Cloud客户添加了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/security-enforcement-policy">安全策略： </a>必需的操作和截止日期，以说明在运行不支持的版本或第三方软件依赖项的云部署上升级Adobe Commerce的要求、时间表和说明。</p>
</td>
      <td>
        新主题
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b7649aae1f8cab020c1081db2b2363bca22adfed">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月28日

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
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805">ACP2E-4805的QPT 1.1.82修复程序的详细说明：当第一个可销售子项稍后出现在列表</a>中时，可配置产品的签出请求速度会变慢。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1b5fb4826f6599d7b7609dedfeb545f29454ba4d">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748">ACP2E-4748的QPT 1.1.82修复的详细说明：奖励点过期时间在具有大量奖励点历史记录</a>的商店上运行缓慢。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/30fe149f9743ceca7f40374246b4fc9b9503c590">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875">ACP2E-4875的QPT 1.1.82修复程序的详细说明：打开具有大量通讯簿的客户帐户</a>时，管理员用户注销。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3174f84e0a8c64aaed50cc075a9287bc011778ef">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月27日

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
      <td><p>添加了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/overview">Overview： Quality Patches Tool (QPT) v1.1.82</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ddfb8e85d015b8ab675a3af56cf5d2bb72e535c4">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月23日

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
      <td><p>更新了Adobe Commerce 2.4.9的MariaDB Cloud版本支持详细信息中的<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">系统要求</a>（建议使用12.3，支持使用11.8）。</p>
</td>
      <td>
        技术
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/eaf47339d87d296799367f699f9322c14e6ee780">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月22日

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
      <td><p>使用最新的Commerce on Cloud Service版本（包括RabbitMQ 4.3更新并确认与MariaDB 12.3的兼容性）更新了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">系统要求</a>主题。</p>
</td>
      <td>
        重大更新
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6607852ba3221a1120f3c88007c106ed9704dcec">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月21日

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
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4401">ACP2E-4401的QPT 1.1.81修复程序的详细说明：可配置产品的主页的计划更新预览重定向到维护页</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/41aac13f73ff0836f93b8ec30a709bd89fa34a94">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4468">ACP2E-4468的QPT 1.1.81修复程序的详细说明：网站范围内的管理员用户无法在页面生成器</a>中保存动态块。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/f5fbe594284c05aaa9b2461e3628a3444229efb6">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月16日

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
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4801">ACP2E-4801的QPT 1.1.81修复的详细说明：在Admin</a>中重新配置可转让报价时，捆绑产品选项数量不会更新。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/31872eee953126b52f1c13444dd46140edc879c6">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4786">ACP2E-4786的QPT 1.1.81修复的详细说明：配置AWS S3远程存储时，产品导出失败</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b7ca2e40743aa512b0bc785e486d3e7d1c6dbefc">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月15日

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
      <td><p>添加了有关<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4630">ACP2E-4630的QPT 1.1.81修复程序的详细说明：长产品名称在分页符</a>后与多页销售PDF中的相邻列重叠。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5581e6f7a507bb83a3fc0fd7229239137b15acd7">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月14日

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
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4300">ACP2E-4300的QPT 1.1.81修复的详细说明：在管理员客户组发生更改</a>后，店面目录权限未更新。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/2c26efeb7aa734e4dcc8d0131cb82a96d35e8f32">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4680">ACP2E-4680的QPT 1.1.81修复的详细说明：不可销售产品从最终的可转让报价</a>中消失。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1448b291e70cdf515872f019028c15bd703f80fe">提交</a></td>
    </tr>
    <tr>
      <td><p>添加了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro">Commerce版本工具文档</a>，其中包含可用性、报告生成、JSON和CSV输出、疑难解答以及每月报告Adobe Commerce安全修补程序状态的发行说明。</p>
</td>
      <td>
        新主题
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/43571d84d9a27ffa113ba4f3a8a08883602211f6">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月10日

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
      <td><p>添加了<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/overview">Overview： Quality Patches Tool (QPT) v1.1.81</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/2cc434ac8efd0d9344140ad07f2f68d2d48b1fb4">提交</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月6日

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
      <td><p>添加了对<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4493">ACP2E-4493的QPT 1.1.80修复的详细说明：启用异步索引时，“销售订单存档”网格显示不正确的订单状态</a>。</p>
</td>
      <td>
        新主题qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/2fdbf6a4fd4924947a2cb2a508e067b8bb0d694c">提交</a></td>
    </tr>
  </tbody>
</table>
