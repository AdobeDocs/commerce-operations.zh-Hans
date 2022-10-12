---
title: 隐私JavaScript库
description: 了解如何使用自定义工具访问和删除由Adobe Commerce和Magento Open Source收集的客户个人信息。
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# 隐私JavaScript库

隐私JavaScript库是一组工具，可帮助创建访问和删除由Adobe Commerce和Magento Open Source收集的私有数据的流程。

商务数据跟踪服务可以存储适用于隐私法规(如 [《通用数据保护条例》(GDPR)](gdpr.md) 和 [《加州消费者隐私法案》(CCPA)](ccpa.md).

此库提供了一组函数，用于创建隐私数据请求并收集其响应。 使用此库可检索和删除由Adobe Commerce存储在浏览器中的数据，并Magento Open Source数据跟踪服务。

>[!NOTE]
>
>如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 启用，则商务在购物者同意之前不会收集行为数据。 如果 [!UICONTROL **Cookie限制模式**] 默认情况下，商务会收集行为数据。

## 安装

隐私JavaScript库可在以下CDN位置获取： `commerce.adobe.net/magentoprivacy.js`

获取文件后，您需要将其添加到Adobe Commerce或Magento Open Source实例中安装的自定义模块或主题中。 按照 [使用自定义JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 完成此任务的主题。

### 初始化

导入和实例化新 `MagentoPrivacy` 对象或使用 `window` 用于访问隐私JavaScript函数的对象。

示例使用 `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

示例使用 `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用情况

隐私JS库提供了各种函数，用于管理存储在浏览器中的身份数据。

`retrieveIdentity()`
:从浏览器中的服务返回身份对象的JavaScript承诺。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
:从浏览器中的服务中删除身份数据。
此函数为具有 `isDeleted` 布尔属性，指示数据是否已删除。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
