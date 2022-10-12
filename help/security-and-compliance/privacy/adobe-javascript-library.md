---
title: Adobe隐私JavaScript库
description: 了解如何使用自定义工具访问和删除由Adobe Commerce和Magento Open Source收集的客户个人信息。
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Adobe隐私JavaScript库

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

的 [Adobe隐私JavaScript库](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 是一组工具，可帮助创建访问和删除专用数据的流程。

Adobe Commerce和Magento Open Source数据跟踪服务可以存储适用于隐私法规(例如， [《通用数据保护条例》(GDPR)](gdpr.md) 和 [《加州消费者隐私法案》(CCPA)](ccpa.md).

此库提供了一组统一的函数，用于创建隐私数据请求、将其发送到每个产品的实施以及收集响应。 使用此库可通过这些数据跟踪服务检索和删除浏览器中存储的数据。

## 安装

使用以下方法之一下载库文件：

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

获取文件后，您需要将其添加到Adobe Commerce和Magento Open Source实例中安装的自定义模块或主题中。 按照 [使用自定义JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 完成此任务的主题。

## 使用情况

AdobePrivacy JS库提供了各种函数，用于管理存储在浏览器中的身份数据。

`retrieveIdentities()`
:返回服务中的标识数组以及在服务中未找到的标识数组

`removeIdentities()`
:从浏览器中删除标识，并通过 `isDeleteClientSide` 布尔属性，指示数据是否已删除。

`retrieveThenRemoveIdentities()`
:此函数类似于 `removeIdentities()` 在中，它检索一组标识，并从浏览器中将其删除。

有关使用这些函数的更多信息和示例，请参阅 [官方图书馆文档](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### 初始化

实例化新 `AdobePrivacy` 对象来在实施代码中使用AdobePrivacy JS库。

```js
var adobePrivacy = new AdobePrivacy({});
```

该构造函数在实例化过程中接受具有参数的配置对象。
请参阅 [官方图书馆文档](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 以获取这些配置参数的列表。
