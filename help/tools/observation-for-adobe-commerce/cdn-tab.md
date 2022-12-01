---
title: “ [!UICONTROL CDN] 选项卡”
description: 了解 [!UICONTROL CDN] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: 424c832ba7580e5d766dea33e3b776eaca7a0d77
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# 的 [!UICONTROL CDN] 选项卡

此选项卡的信息主要针对 [!DNL content delivery network (CDN)]. 对于Adobe Commerce Cloud，这是 [!DNL Fastly] 服务。

## [!UICONTROL HIT rate]

![点击率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

的 **[!UICONTROL HIT rate]** frame显示可缓存请求的数量，这些请求会导致 [!UICONTROL HITS] 最后一分钟。 这表示缓存成功。 右侧的箭头将显示一周前的同一时间上下的百分比。

## [!UICONTROL HIT Processing]

![点击处理](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

此 **[!UICONTROL HIT processing]** 框显示可缓存请求的数量，这些请求会导致 [!UICONTROL HITS] 在这周。

## [!UICONTROL MISS rate]

![遗漏率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

此 **[!UICONTROL MISS rate]** 框显示可缓存请求在最后一分钟的未命中次数。 如果未缓存请求，并且必须将请求传递到源服务器以提供内容，则会发生错误。 右侧的值是增加/减少与前一周每分钟的分钟数之比。

## [!UICONTROL MISS time]

![错过时间](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![点击率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![错误百分比](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

的 **[!UICONTROL Error Percentage]** 框显示请求的ERROR百分比值，并显示与前一周的同一时间相比的相对增加/减少。

## [!UICONTROL Total Requests]

![总请求数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![错误率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![以秒为单位快速缓存选定时间段的平均响应](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

此帧显示可缓存请求的持续时间（以秒为单位），这意味着如果 `cache_response` 是 [!UICONTROL MISS]，则会显示选定时间内未缓存响应的平均值。

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![由POP分段的选定时间段的快速缓存平均响应（以秒为单位）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![总带宽（所有POP），而1星期前（增加/减少%）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![请求 — 自选定的时间范围与一周前相比起](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

此框架类似于 [!UICONTROL Total Requests] ，但会显示前几周的请求计数。 这些都是请求，而不只是可缓存的请求(其中 `is_cacheable` 为true)。

## [!UICONTROL Response Count]

![响应计数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![按POP划分的带宽](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![前5个URL（5xx或3xx状态代码）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

的 **[!UICONTROL Top 5 URLs]** “视图”显示遇到5xx或3xx错误响应的前5个URL。 由于空间限制，您需要将鼠标悬停在URL上，以查看与该URL关联的特定错误代码。 （例如上图的红色框中）。

## [!UICONTROL Top 25 URLs (200 status)]

![前25个URL（200个状态）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

的 **[!UICONTROL Top 25 URLs]** 框架显示在选定时间范围内按计数返回200个状态的URL。

## [!UICONTROL Duration by Response Status]

![按响应状态划分的持续时间](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

的 **[!UICONTROL Duration by Response Status]** 图表按选定时间范围内的计数显示错误响应，按错误状态代码分面显示。

## [!UICONTROL Duration by Response Status, top 25 urls]

![按响应状态划分的持续时间，前25个URL](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

的 **[!UICONTROL Duration by Response Status, top 25 URLs]** 图表按响应持续时间（以秒为单位）显示前25个URL。 您可能需要将鼠标悬停在URL上才能看到整个路径。 此外，要删除除一个URL之外的所有URL，请单击该URL。 然后，您可以通过单击其他URL来逐个添加回来。 如果要删除单个URL，可以按住键并单击每个URL以从图表中删除它们。

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![持续时间（按响应状态），前25个非200个状态](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

的 **[!UICONTROL Duration by Response Status, top 25 non-200 status]** 图表与最后一个图表类似，只是焦点在非200个状态代码或错误状态代码上。 它将显示错误代码，然后显示URL。 您可能需要将鼠标悬停在URL上才能看到整个路径。 此外，要删除除一个URL之外的所有URL，请单击该URL。 然后，您可以通过单击其他URL来逐个添加回来。 如果要删除单个URL，可以按住键并单击每个URL以从图表中删除它们。

## [!UICONTROL Error Count by POP timeline]

![按POP时间轴计错](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

的 **[!UICONTROL Error Count by POP timeline]** 图表按错误代码显示错误状态在选定时间轴上的计数。

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![按响应状态划分的持续时间、前25个客户端IP、非200个状态](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

的 **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** 图表按选定时间范围内存在状态错误代码的平均持续时间显示IP地址。

## [!UICONTROL IP Frequency]

![IP频度](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

的 **[!UICONTROL IP Frequency]** frame会计算来自 [!DNL Fastly] 日志。 具有这些状态的Web请求将到达源服务器并将向服务器添加负载。 它以频度显示排名前20的地址。 此框架可用于检测网站上的IP攻击或重负载源。 此图表也显示在“摘要”选项卡中，放在此处，以便与 [!DNL Fastly] 此选项卡上显示的日志信息。
