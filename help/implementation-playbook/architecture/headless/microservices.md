---
title: Adobe Commerce微服務
description: 能夠區分Headless和微服務，因為它與Adobe Commerce相關。
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Headless和微服務

切勿將Headless與微服務混淆。 很多時候，我們會在與Headless相同的句子中聽到關於微服務的對話。 它們是完全不同的事物。 它們可以搭配使用，但概念完全不同。

微服務架構是一個術語，用來描述將應用程式分割成一組較小且鬆散耦合服務的做法。 微服務可讓個別後端服務變成：

- **彼此隔離** — 例如，定價服務與目錄服務沒有相依性。

- **部署單點** — 客戶只部署他們需要的應用程式部分。

- **獨立縮放** — 可以將資源指派給高需求的服務，例如庫存查詢。

- **自主開發** — 可彼此獨立開發及部署。

微服務與斬去商務棧疊或API的頭沒有關係。 當我們思考核心程式碼中位於Adobe Commerce後台的商務服務時，我們要將這些服務彼此隔離。 因此，微服務架構正在鬆散地分解所有這些服務，例如定價服務、目錄服務和存貨服務，並且使每一個服務彼此隔離。

微服務可獨立擴充及自主開發。 微服務類似於多租使用者SaaS開發程式。 許多現代的多租使用者SaaS產品都是使用多服務方法開發的。 甚至Adobe自己的SaaS產品（例如Order Management）、新型AI驅動的Product Recommendations工具，以及Adobe Commerce的其他SaaS元件，都透過微服務方法進行開發。 需要澄清的是，Adobe Commerce 2.4.x並非微服務架構，而是Headless架構。
