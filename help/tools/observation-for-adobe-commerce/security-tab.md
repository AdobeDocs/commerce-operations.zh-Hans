---
title: '[!UICONTROL Security]选项卡'
description: 了解 [!DNL Observation for Adobe Commerce]的[!UICONTROL Security]选项卡。
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!UICONTROL Security]选项卡

**[!UICONTROL Security]**&#x200B;选项卡说明了安全问题并隔离了其潜在原因。 此外，还描述了所述标签的帧。

## [!UICONTROL API calls by IP, details by URL]

**[!UICONTROL API calls by IP, details by URL]**&#x200B;帧显示选定时间范围内按IP进行的API调用数。 此帧显示IP地址以及该IP地址访问的API URL。

通过IP进行![API调用](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

**[!UICONTROL Forgot Password]**&#x200B;访问帧显示选定时间范围内忘记密码尝试的次数。 针对IP地址的高活动可能是对站点的攻击。

![忘记密码](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

**[!UICONTROL Create Account access]**&#x200B;框架显示选定时间范围内新帐户活动的数量。 单个IP地址的活动频繁可能表示存在攻击。

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

**[!UICONTROL POST activities]**&#x200B;框架显示网站的`POST`活动，从[!DNL Fastly]日志刻面到`client_ip`。 它还显示了IP地址访问的URL。

![POST活动](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

**[!UICONTROL POST activities summary table]**&#x200B;框架显示网站的摘要`POST`活动，从[!DNL Fastly]日志刻面到`client_ip`。 它还显示由IP地址访问的URL的计数。 该计数针对选定的时间范围。

![POST — 活动 — 摘要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

**[!UICONTROL POST activities details table]**&#x200B;框架显示[!DNL Fastly]日志中网站的`POST`活动。 它还显示了[!DNL Fastly]日志中有关这些请求的所有详细信息。 仅限于最近2000个请求。
![POST — 活动 — 详细信息](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

**[!UICONTROL Guest Carts activities]**&#x200B;帧显示选定时间范围内的访客购物车活动数，按IP地址和访问的URL分面。 客人购物车可用于梳理攻击。 此框架显示访问访客购物车URL的请求总数。

![来宾购物车活动](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

**[!UICONTROL API – forgot password, create account by Countries]**&#x200B;框架显示所选时间范围内已创建的帐户数以及重置忘记密码的请求数。 此外，还会显示请求的原产国。 此框架侧重于请求的来源国。

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

**[!UICONTROL API - forgot password, create account by Countries and IP address]**&#x200B;框架显示所选时间范围内已创建的帐户数以及重置忘记密码的请求数。 它面向以显示IP地址、访问的URL以及请求的原产国。 此帧重点关注IP计数。

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

**[!UICONTROL Guest cart activities by IP]**&#x200B;帧显示选定时间范围内按IP的访客购物车活动。

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

**[!UICONTROL Guest cart activities by Countries]**&#x200B;框架显示选定时间范围内各个国家/地区的访客购物车活动。

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
