---
title: AEM性能优化
description: 优化默认的Adobe Experience Manager配置以支持Adobe商务的高负载。
source-git-commit: 63f153365398c3ae7dc7e6214b67705c8a4c7686
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# AEM性能优化

AEM Dispatcher是一个反向代理，可帮助交付既快速又动态的环境。 它作为静态HTML服务器（如Apache HTTP Server）的一部分使用，其目的是以静态资源的形式尽可能多地存储（或“缓存”）站点内容。 此方法旨在尽可能减少访问AEM页面渲染功能和Adobe商务GraphQL服务的需求。 将大部分页面作为静态HTML、CSS和JS提供的结果，可为用户带来性能优势，并降低环境中的基础架构要求。 缓存时，应考虑用户之间可能重复相同的任何页面或查询。

以下各节在较高级别显示了建议的技术重点领域，这些重点领域有待审核，以便在CIF/Adobe商务环境中对AEM进行有效缓存。

## 基于TTL的AEM调度程序缓存

在调度程序上尽可能多地缓存网站是任何AEM项目的最佳做法。 如果使用基于时间的缓存失效，则会在设定的有限时间内缓存服务器端呈现的CIF页面。 设置时间过期后，下一个请求将从AEM发布者和Adobe商务GraphQL中重建页面，并将其再次存储在调度程序缓存中，直到下次失效为止。

TTL缓存功能可在AEM中使用ACS AEM Commons包中的“Dispatcher TTL”组件配置，并在dispatcher.any配置文件中设置/enableTTL &quot;1&quot;。

如果启用，调度程序将从后端评估响应标头，如果响应标头包含“缓存控制”的最大使用日期或过期日期，则会创建缓存文件旁边的辅助空文件，修改时间等于到期日期。 在修改时间之后请求缓存文件时，会自动从后端重新请求缓存文件。 这提供了一种有效的缓存机制，一旦业务利益相关方确认并接受产品更新延迟(TTL)，就无需手动干预或维护。

## 浏览器缓存

上述调度程序TTL方法将大大减少请求和对发布程序的负载，但是有一些资产很不可能更改，因此甚至对调度程序的请求也可以通过在用户浏览器上本地缓存相关文件来减少。 例如，网站的徽标显示在网站模板中网站的每个页面上，无需每次向调度程序请求徽标。 而是可以存储在用户的浏览器缓存中。 每次页面加载的带宽要求降低会对站点响应性和页面加载时间产生重大影响。

浏览器级别的缓存通常通过“Cache-Control:max-age=”响应标头。 最大值设置告知浏览器在尝试“重新验证”或再次从网站请求文件之前，应缓存文件的秒数。 缓存最大时间的这一概念通常称为“缓存过期”或TTL（“存留时间”）。 大规模提供商务体验 — 使用Adobe Experience Manager、Commerce Integration Framework、Commerce 7Adobe

AEM/CIF/Adobe商务网站的一些区域（可设置为在客户端的浏览器中缓存）包括：

- 图像(在AEM模板本身中，例如网站徽标和模板设计图像 — 目录产品图像将通过Fastly从Adobe商务中调用，稍后将讨论缓存这些图像)
- HTML文件（适用于不常更改的页面 — 条款和条件页面等）
- CSS文件
- 所有网站JavaScript文件 — 包括CIF JavaScript文件

## 调度程序静态文件级别和宽限期优化

默认的Dispatcher配置使用/statfilelevel &quot;0&quot;设置 — 这表示单个“.stat”文件位于htdocs目录（文档根目录）的根目录中。 如果对AEM中的页面或文件进行了更改，则此单个stat文件的修改时间将更新为更改时间。 如果时间比资源的修改时间新，则调度程序将考虑所有资源都将失效，对无效资源的任何后续请求都将触发对Publish实例的调用。 因此，基本上，通过此设置，每次激活都会使整个缓存失效。

对于任何网站（尤其是负载较重的商务网站），这会给AEM发布层带来不必要的负载，使整个站点结构仅通过一次页面更新而失效。

相反，可以将statfilelevel设置修改为与文档根目录htdocs目录中子目录的深度对应的更高值，以便当位于某个级别的文件失效时，只更新该.stat目录级别及以下级别的文件。

例如：假设您的产品页面模板位于：

```
content/ecommerce/us/en/products/product-page.html
```

每个文件夹级别都将具有“stat级别” — 如上表中所示。

| 内容(docroot) | 电子商务 | us | en | 产品 | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 3 | 2 | 3 | 4 | - |

在这种情况下，如果您将statfilelevel属性设置为默认的&quot;0&quot;，并且product-page.html模板已更新并激活，从而触发失效，则从docroot到4级的每个.stat文件都将被处理，并且文件失效，从而导致AEM发布实例对该单次更改提出进一步请求，以用于站点中所有页面（包括其他网站、国家/地区和语言）。

但是，如果将statfilelevel属性设置为4级，并对product-page.html进行了更改，则只会处理该特定网站/国家/语言产品目录中的.stat文件。

请注意，不应将.stat文件级别设置为过高级别 — 超过20可能会影响性能。 在运行性能测试时执行批量文件激活，应该为您提供应将状态级别调整为的正确级别。

配置statfilelevel时要优化的另一个调度程序设置是宽限期设置。 此值定义在上次激活后，仍可从缓存中提供失效的失效资源的秒数。 自动失效的资源因任何激活（当其路径与调度程序/无效部分匹配时，以及与statfileslevel属性中指定的级别匹配时）而失效。 将宽限期设置设置为2秒可用于防止出现以下情况：即使发布者仍在构建新页面过程中，仍会向发布者持续发送多个请求。

>[!NOTE]
>
> [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub存储库中提供了有关此主题的更多详细信息。

## CIF — 通过组件进行GraphQL缓存

可以将AEM中的各个组件设置为缓存，这意味着要Adobe的GraphQL请求
Commerce被调用一次，然后从AEM缓存中检索后续请求（符合配置的时间限制），而不会在AdobeCommerce上进一步加载。 例如，网站导航基于每个页面上显示的类别树以及多面搜索功能中的选项 — 这两个区域只需对Adobe商务进行资源密集型查询即可构建，但不太可能定期更改，因此是缓存的好选项。 例如，即使发布者正在重建PDP或PLP，对导航构建占用大量资源的GraphQL请求也不会命中Adobe商务，并且可以从AEM CIF上的GraphQL缓存中进行检索。

以下示例用于缓存导航组件，因为它在站点的所有页面上发送相同的GraphQL查询。 以下请求会缓存导航结构过去100个条目10分钟：

```
venia/components/structure/navigation:true:100:600
```

以下示例在搜索页面中缓存了过去100个多面搜索选项，时间为1小时：

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

请求（包括所有自定义http标头和变量）必须完全匹配，才能使缓存“点击”，并防止重复调用Adobe商务。 应当注意，一旦设置，就无法轻松地手动使此缓存失效。 这可能意味着，如果在Adobe商务中添加了新类别，则在上述缓存中设置的到期时间到期并刷新GraphQL请求之前，该类别不会开始显示在导航中。 搜索彩块化的情况相同。 但是，鉴于此缓存可实现的性能优势，这通常是可接受的折中方案。

可以使用“GraphQL客户端”中的AEM OSGi配置控制台来设置上述缓存选项
配置工厂”。 可以使用以下格式指定每个缓存配置条目：

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## 混合缓存 — 缓存的调度程序页面中的客户端GraphQL请求

还可以采用混合方法来缓存页面：CIF页面可能包含组件，组件始终会直接从Adobe的浏览器请求客户商务的最新信息。 这对于模板中页面的特定区域非常有用，因为这些区域需要通过实时信息保持最新：例如，PDP中的产品价格。 当价格因动态价格匹配而频繁更改时，该信息可以配置为不会缓存在调度程序上，而是可以在客户浏览器中通过带有AEM CIF Web组件的GraphQL API直接从Adobe商务中获取价格。

可以通过AEM组件设置进行配置 — 对于产品列表页面上的价格信息，可以在产品列表模板中进行配置，在页面设置中选择产品列表组件并选中“加载价格”选项。 同样的方法也适用于库存水平。

仅当需要实时、不断地更新信息时，才应使用上述方法。 在上例中，与定价一起，可以与业务利益相关方商定，仅在低流量时每天更新价格，然后执行缓存刷新操作。 这样，在构建显示定价信息的每个页面时，就不再需要实时定价信息请求以及Adobe商务的后续额外负载。

## 不可执行的GraphQL请求

页面中的特定动态数据组件不应缓存，且将始终需要GraphQL调用来Adobe商务，例如，对于购物车和整个结帐页面的调用。 此信息是特定于用户的，并且会因客户在网站上的活动而不断更改 — 例如，通过将产品添加到其购物车。

如果网站的设计根据用户的角色给出不同的响应，则不应为已登录的客户缓存GraphQL查询结果。 例如，您可以创建多个客户群组，并为每个群组设置不同的产品价格或不同的产品类别可见性。 此类缓存结果可能会导致客户查看另一个客户组的价格或显示不正确的类别。

## 忽略AEM Dispatcher缓存上的跟踪参数

电子商务网站可能会使用PPC搜索广告或社交媒体促销活动来吸引其网站的流量。

使用这些媒介意味着将跟踪ID添加到该平台的出站链接上。 例如，Facebook将在URL中添加Facebook点击ID(fbclid),Google Addies将添加Google点击ID(gclid)，这会使到AEM前端的传入链接如下所示：

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

gclid和fbclid将随每位单击广告的用户而发生更改，这用于跟踪目的，但使用其默认设置，AEM会将每个请求视为唯一页面，绕过调度程序，在发布者和Adobe商务上产生不必要的额外负载。

在剧增事件期间，这甚至可能导致AEM发布者变得过载且无响应。 如果将某个页面的参数设置为忽略，则在首次请求页面时会缓存该页面。 无论请求中的参数值如何，缓存的页面都会提供该页面的后续请求。

>[!NOTE]
>
>[aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub存储库中提供了有关设置`ignoreUrlParams`的重要性的进一步阅读。

因此，应将其配置为在默认情况下忽略“ignoreUrlParams”中的所有参数，除非使用了GET参数来更改页面的HTML结构。 例如，搜索页面中的搜索词在URL中作为GET参数显示 — 在这种情况下，您应手动配置ignoreUrlParams以忽略广告渠道所使用的gclid、fbclid和任何其他跟踪参数等参数，从而使正常网站操作所需的GET参数不受影响。

## MPM工作程序对调度程序的限制

MPM工作程序设置是一种高级Apache HTTP服务器配置，需要进行彻底测试，才能根据Dispatcher的可用CPU和RAM进行优化。 但是，在本白皮书的范围中，我们建议将ServerLimit和MaxRequestWorkers增加到服务器可用CPU和RAM支持的级别，然后将MinSpareThreads和MaxSpareThreads都增加到与MaxRequestWorkers匹配的级别。

此配置会将Apache HTTP保留为“完全就绪设置”，该设置是适用于具有大量RAM和多个CPU核心的服务器的高性能配置。 此配置将通过维护永久开放连接来准备提供请求，从Apache HTTP生成尽可能最佳的响应时间，并消除因突发流量激增（如在闪存销售期间）而生成新进程的任何延迟。
