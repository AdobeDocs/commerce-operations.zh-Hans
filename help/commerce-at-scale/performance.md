---
title: AEM性能优化
description: 优化默认Adobe Experience Manager配置以支持Adobe Commerce上的高负载。
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# AEM性能优化

AEM Dispatcher是一个反向代理，可帮助提供快速且动态的环境。 它作为静态HTML服务器（例如Apache HTTP Server）的一部分工作，旨在以静态资源的形式存储（或“缓存”）尽可能多的站点内容。 此方法旨在尽可能减少访问AEM页面渲染功能和Adobe Commerce GraphQL服务的需要。 将许多页面作为静态HTML、 CSS和JS提供服务的结果为用户提供了性能优势，并降低了对环境的基础架构要求。 对于任何可能在不同用户之间重复出现的页面或查询，应考虑进行缓存。

以下部分从较高层面说明了需要审查的建议技术重点领域，以便在CIF/Adobe Commerce环境中启用AEM上的有效缓存。

## AEM Dispatcher上基于TTL的缓存

对于任何AEM项目，最佳做法是在调度程序上尽可能多地缓存站点。 使用基于时间的缓存失效将在设定的有限时间内缓存服务器端渲染的CIF页面。 设置时间过期后，下一次请求将从AEM发布者和Adobe Commerce GraphQL重新构建页面，并将其再次存储在Dispatcher缓存中，直到下一次失效。

在AEM中，可以使用ACS AEM Commons包中的“Dispatcher TTL”组件并在dispatcher.any配置文件中设置/enableTTL &quot;1&quot;来配置TTL缓存功能。

如果启用，Dispatcher将从后端评估响应标头，如果其中包含Cache-Control max-age或过期日期，则将在缓存文件旁边创建一个辅助空文件，其修改时间等于过期日期。 在修改时间过后请求缓存的文件时，将自动从后端重新请求该文件。 这提供了一种有效的缓存机制，在产品更新延迟(TTL)得到业务利益相关者的认可和接受后，无需手动干预或维护。

## 浏览器缓存

上述Dispatcher TTL方法可显着减少请求并减轻发布者的负载，但有些资产极不可能更改，因此，甚至可以通过在用户浏览器中本地缓存相关文件来减少对Dispatcher的请求。 例如，站点的徽标（显示在站点模板中站点的每个页面上）不需要每次都向Dispatcher请求。 而是可以存储在用户的浏览器缓存中。 降低每个页面加载的带宽需求将对站点响应性和页面加载时间产生重大影响。

通常，浏览器级别的缓存是通过“Cache-Control： max-age=”响应标头来设置。 maxage设置可告知浏览器，在尝试“重新验证”或再次从站点请求缓存之前，它应该缓存文件的时间长度（以秒为单位）。 这个缓存max-age的概念通常称为“缓存过期”或TTL（“生存时间”）。 大规模交付Commerce体验 — 使用Adobe Experience Manager、Commerce Integration Framework、Adobe Commerce 7

可以设置为在客户端浏览器中缓存的AEM/CIF/Adobe Commerce站点的某些区域包括：

- 图像(在AEM模板本身中，例如网站徽标和模板设计图像 — 将通过Fastly从Adobe Commerce调用目录产品图像，稍后将讨论缓存这些图像)
- HTML文件（用于不常更改的页面 — 条款和条件页面等）
- CSS文件
- 所有站点JavaScript文件 — 包括CIF JavaScript文件

## Dispatcher statfilelevel和宽限期优化

默认Dispatcher配置使用/statfilelevel &quot;0&quot;设置 — 这意味着单个&quot;。stat&quot;文件放在htdocs目录（文档根目录）的根目录下。 如果对AEM中的页面或文件进行了更改，则此单一stat文件的修改时间将更新为更改时间。 如果时间比资源的修改时间新，则Dispatcher将认为所有资源都失效，并且任何对失效资源的后续请求都将触发对发布实例的调用。 因此，基本上，使用此设置，每次激活都会使整个缓存失效。

对于任何网站（尤其是负载沉重的商务网站），这将给AEM发布层带来不必要的负载，以便整个网站结构在仅进行单页更新时失效。

相反，statfilelevel设置可以修改为更高的值，对应于文档根目录下htdocs目录中的子目录的深度，这样，当位于特定级别的文件失效时，将只更新该.stat目录级别和更低级别的文件。

例如：假设您有一个产品页面模板：

```
content/ecommerce/us/en/products/product-page.html
```

每个文件夹级别都将具有“stat level” — 如上表所划分的那样。

| 内容(docroot) | 电子商务 | us | en | 产品 | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

在这种情况下，如果您将statfilelevel属性保留为默认的“0”，并更新和激活了product-page.html模板以触发失效操作，则将接触从docroot到级别4的每个.stat文件，使文件失效，从而导致AEM发布实例进一步请求网站上的所有页面（包括其他网站、国家/地区和语言）从该单次更改中生效。

但是，如果statfilelevel属性设置为level 4，并且对product-page.html进行了更改，则只接触该特定网站/国家/地区/语言的products目录中的.stat文件。

请注意，不应将.stat文件级别设置为太高的级别 — 超过20可能会影响性能。 在运行性能测试时执行批量文件激活应该为您提供应将stat级别调整到的正确级别。

配置statfilelevel时要优化的另一个dispatcher设置是gracePeriod设置。 这定义在上次激活发生后，过时的、自动失效的资源仍可从缓存中获得服务的秒数。 任何激活都会使自动失效的资源失效（当其路径与dispatcher /invalidate部分匹配以及与statfileslevel属性中指定的级别匹配时）。 将gracePeriod设置设置为2秒可用于防止出现以下情况：即使发布者仍在构建新页面，仍会持续向发布者发送多个请求。

>[!NOTE]
>
> 有关此主题的更多详细阅读，请参见 [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub存储库

## CIF — 通过组件进行GraphQL缓存

可以将AEM中的各个组件设置为缓存，这意味着对Adobe Commerce的GraphQL请求调用一次，然后从AEM缓存中检索后续请求，最多（在配置的时间限制内），并且不会将进一步的加载放置到Adobe Commerce上。 例如，基于每个页面上显示的类别树的站点导航和多面搜索功能中的选项 — 这仅仅是两个需要在Adobe Commerce上构建资源密集型查询的区域，但不太可能定期更改，因此将是缓存的良好选择。 这样，即使发布者正在重建PDP或PLP，用于导航构建的资源密集型GraphQL请求也不会命中到Adobe Commerce，并且可从AEM CIF上的GraphQL缓存中检索。

以下示例适用于要缓存的导航组件，因为它在网站的所有页面上发送相同的GraphQL查询。 对于导航结构，以下请求会在10分钟内缓存过去100个条目：

```
venia/components/structure/navigation:true:100:600
```

下面的示例在搜索页面中缓存过去100个分面的搜索选项1小时：

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

请求（包括所有自定义http标头和变量）必须完全匹配，缓存才能“点击”，并防止重复调用Adobe Commerce。 需要注意的是，一旦设置，就没有简单的方法可手动使此缓存失效。 这可能意味着，如果在Adobe Commerce中添加新类别，则在上面缓存中设置的到期时间已过期并刷新GraphQL请求之前，此类别不会开始显示在导航中。 搜索Facet也是这样。 但是，鉴于此缓存可带来的性能优势，这通常是可接受的折衷方案。

上述缓存选项可以使用“GraphQL客户端配置工厂”中的AEM OSGi配置控制台进行设置。 可以使用以下格式指定每个缓存配置条目：

```
* NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## 混合缓存 — 缓存的Dispatcher页面中的客户端GraphQL请求

也可以使用混合方法缓存页面：CIF页面可以包含始终直接从客户浏览器从Adobe Commerce请求最新信息的组件。 这对于模板中页面的特定区域非常有用，这些区域对于及时了解实时信息非常重要：例如PDP中的产品价格。 如果价格由于动态价格匹配而经常变化，则可以将该信息配置为不在Dispatcher上缓存，而是在客户的浏览器中，通过带AEM CIF Web组件的GraphQL API，直接从Adobe Commerce中获取价格。

这可以通过AEM组件设置进行配置 — 对于产品列表页面上的价格信息，可以在产品列表模板中进行配置，在页面设置中选择产品列表组件，然后选中“加载价格”选项。 同样的方法也适用于库存水平。

上述方法只应在需要实时、不断更新信息的情况下使用。 在上面的定价示例中，可能与业务利益相关者达成一致意见，即在低流量时间每天更新价格并执行缓存刷新操作。 这样一来，在构建每个显示定价信息的页面时，就不需要实时的定价信息请求，也就不需要在Adobe Commerce上额外加载定价信息。

## 不可缓存的GraphQL请求

不应缓存页面中的特定动态数据组件，这些组件将始终要求GraphQL调用Adobe Commerce，例如针对购物车以及整个结帐页面的调用。 此信息特定于用户，并且会因客户在网站上的活动（例如，将产品添加到其购物车）而不断变化。

如果网站的设计会根据用户的角色提供不同的响应，则不应为已登录的客户缓存GraphQL查询结果。 例如，您可以创建多个客户组，并为每个组设置不同的产品价格或不同的产品类别可见性。 缓存此类结果可能会导致客户看到其他客户组的价格或显示不正确的类别。

## 忽略AEM Dispatcher缓存上的跟踪参数

电子商务网站可能会使用PPC搜索广告或社交媒体促销活动来增加其网站的流量。

使用这些媒体意味着将跟踪ID添加到来自该平台的出站链接中。 例如，Facebook会将Facebook点击ID (fbclid)添加到URL，Google Adverts会添加Google点击ID (gclid)，这会使到您的AEM前端的传入链接如下所示，例如：

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

gclid和fbclid将随每个单击该广告的用户而更改，这用于跟踪目的，但通过默认设置，AEM会将每个请求视为一个唯一的页面，这会绕过调度程序，并给发布者和Adobe Commerce产生不必要的额外负载。

在激增事件期间，这甚至可能导致AEM发布者过载且无响应。 将某个参数设置为忽略某个页面时，将会在首次请求该页面时缓存该页面。 无论请求中的参数值如何，都将为该页面的后续请求提供缓存页面。

>[!NOTE]
>
>进一步了解设置的重要性 `ignoreUrlParams` 可在 [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub存储库

因此，应将其配置为默认忽略“ignoreUrlParams”中的所有参数，除非使用的是GET参数，这会更改页面的HTML结构。 例如，在URL中搜索词作为GET参数的搜索页面就是这种情况，在这种情况下，您应该手动配置ignoreUrlParams以忽略gclid、fbclid等参数以及您的广告渠道正在使用的任何其他跟踪参数，从而使正常网站操作所需的GET参数不受影响。

## MPM工作人员对Dispatcher的限制

MPM工作程序设置是一种高级Apache HTTP服务器配置，它需要彻底的测试，以根据Dispatcher的可用CPU和RAM进行优化。 但是，在本白皮书中，我们建议ServerLimit和MaxRequestWorker应提高到服务器可用CPU和RAM支持的级别，然后MinSpareThreads和MaxSpareThreads都提高到与MaxRequestWorker匹配的级别。

此配置会将Apache HTTP保留在“完全就绪设置”上，这是具有大量RAM和多CPU核心的服务器的高性能配置。 此配置将通过保持随时准备处理请求的持久开放连接，从Apache HTTP生成最佳响应时间，并将消除在响应突发流量激增时派生新进程的任何延迟，例如在闪存销售期间。
