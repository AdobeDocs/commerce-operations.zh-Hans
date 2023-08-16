---
title: 此 [!UICONTROL Security] 选项卡
description: 了解 [!UICONTROL Security] 选项卡/ [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 此 [!UICONTROL Security] 选项卡

此 **[!UICONTROL Security]** 选项卡说明了安全问题并隔离了其潜在原因。 此外，还描述了所述标签的帧。

## [!UICONTROL API calls by IP, details by URL]

此 **[!UICONTROL API calls by IP, details by URL]** 此帧显示选定时间范围内按IP进行的API调用数。 此帧显示IP地址以及该IP地址访问的API URL。

![按IP进行的API调用](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

此 **[!UICONTROL Forgot Password]** 访问帧显示选定时间范围内忘记密码尝试的次数。 针对IP地址的高活动可能是对站点的攻击。

![忘记密码](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

此 **[!UICONTROL Create Account access]** 框架显示选定时间范围内的新客户活动数量。 单个IP地址的活动频繁可能表示存在攻击。

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

此 **[!UICONTROL POST activities]** 框架显示 `POST` 网站的活动，面向 `client_ip` 从 [!DNL Fastly] 日志。 它还显示了IP地址访问的URL。

![POST活动](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

此 **[!UICONTROL POST activities summary table]** 框架显示摘要 `POST` 网站的活动，面向 `client_ip` 从 [!DNL Fastly] 日志。 它还显示由IP地址访问的URL的计数。 该计数针对选定的时间范围。

![POST — 活动 — 摘要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

此 **[!UICONTROL POST activities details table]** 框架显示 `POST` 网站的活动 [!DNL Fastly] 日志。 它还会显示来自以下位置的所有详细信息： [!DNL Fastly] 记录这些请求。 仅限于最近2000个请求。
![POST — 活动 — 详细信息](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

此 **[!UICONTROL Guest Carts activities]** 帧显示选定时间范围内访客购物车活动的数量，按IP地址和访问的URL分面。 客人购物车可用于梳理攻击。 此框架显示访问访客购物车URL的请求总数。

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

此 **[!UICONTROL API – forgot password, create account by Countries]** 框架显示所选时间范围内创建的帐户数以及重置忘记密码的请求数。 此外，还会显示请求的原产国。 此框架侧重于请求的来源国。

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

此 **[!UICONTROL API - forgot password, create account by Countries and IP address]** 框架显示所选时间范围内创建的帐户数以及重置忘记密码的请求数。 它面向以显示IP地址、访问的URL以及请求的原产国。 此帧重点关注IP计数。

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

此 **[!UICONTROL Guest cart activities by IP]** 此框架显示选定时间范围内按IP划分的访客购物车活动。

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

此 **[!UICONTROL Guest cart activities by Countries]** 框架显示选定时间范围内按国家/地区划分的访客购物车活动。

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
