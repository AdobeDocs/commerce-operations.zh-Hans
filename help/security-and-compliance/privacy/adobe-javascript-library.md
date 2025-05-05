---
title: Adobe隐私JavaScript库
description: 了解如何使用自定义工具访问和删除Adobe Commerce收集的客户个人信息。
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe隐私JavaScript库

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

[Adobe隐私JavaScript库](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=zh-Hans)是一组工具，可帮助创建访问和删除专用数据的流程。

Adobe Commerce数据跟踪服务可以存储适用于隐私法规的隐私信息，例如[通用数据保护条例(GDPR)](gdpr.md)和[加州消费者隐私法案(CCPA)](ccpa.md)。

此库提供了一组统一的功能，可用于创建隐私数据请求、将这些请求发送到每个产品的实施以及收集响应。 使用此库检索和删除这些数据跟踪服务存储在浏览器中的数据。

## 安装

使用以下方法之一下载库文件：

- npm： `npm install @adobe/adobe-privacy`
- GitHub： [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

获得文件后，您需要将其添加到Adobe Commerce实例中安装的自定义模块或主题。 按照[使用自定义JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/)主题中所述的说明完成此任务。

## 使用情况

AdobePrivacy JS库提供了多种功能，用于管理存储在浏览器中的身份数据。

`retrieveIdentities()`
：从服务返回标识数组，以及未在服务中找到的标识数组

`removeIdentities()`
：从浏览器中删除身份并返回一个身份对象数组，其中包含`isDeleteClientSide`布尔属性以指示数据是否已删除。

`retrieveThenRemoveIdentities()`
：此函数与`removeIdentities()`类似，因为它检索一组标识并从浏览器中删除它们。

有关使用这些函数的更多信息和示例，请参阅[官方库文档](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=zh-Hans)。

### 初始化

实例化新的`AdobePrivacy`对象以在实施代码中使用AdobePrivacy JS库。

```js
var adobePrivacy = new AdobePrivacy({});
```

构造函数在实例化期间接受带有参数的配置对象。
有关这些配置参数的列表，请参阅[官方库文档](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=zh-Hans)。
