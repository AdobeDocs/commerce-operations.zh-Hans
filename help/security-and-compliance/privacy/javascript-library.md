---
title: 隐私JavaScript库
description: 了解如何使用自定义工具访问和删除Adobe Commerce收集的客户个人信息。
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# 隐私JavaScript库

隐私JavaScript库是一组工具，可帮助创建用于访问和删除Adobe Commerce收集的私有数据的流程。

Commerce数据跟踪服务可以存储适用于隐私法规的隐私信息，例如[通用数据保护条例(GDPR)](gdpr.md)和[加州消费者隐私法案(CCPA)](ccpa.md)。

此库提供了一组用于创建隐私数据请求和收集其响应的功能。 使用此库可检索和删除Adobe Commerce数据跟踪服务存储在浏览器中的数据。

>[!NOTE]
>
>如果启用了[Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=zh-Hans)，则在购物者同意之前，Commerce不会收集行为数据。 如果&#x200B;[!UICONTROL **Cookie限制模式**]&#x200B;被禁用，Commerce将默认收集行为数据。

## 安装

隐私JavaScript库在以下位置提供： `commerce.adobe.net/magentoprivacy.js`

获得文件后，您需要将其添加到Adobe Commerce实例中安装的自定义模块或主题。 按照[使用自定义JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/)主题中所述的说明完成此任务。

### 初始化

导入并实例化新的`MagentoPrivacy`对象，或使用`window`对象访问隐私JavaScript功能。

使用`import`的示例：

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

使用`window`的示例：

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用情况

隐私JS库提供了多种功能，用于管理存储在浏览器中的身份数据。

`retrieveIdentity()`
：从浏览器中的服务返回标识对象的JavaScript promise 。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
：从浏览器中的服务删除身份数据。
此函数为具有`isDeleted`布尔属性的标识对象返回JavaScript promise，以指示数据是否已删除。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
