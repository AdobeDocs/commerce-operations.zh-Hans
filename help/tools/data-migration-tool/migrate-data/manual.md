---
title: 需要手动迁移的数据
description: '了解在Magento1中必须手动迁移才能Magento2数据迁移的数据，以及如何执行迁移。 '
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 需要手动迁移的数据

需要手动迁移四种类型的数据：

* 媒体

* [店面](https://glossary.magento.com/storefront) 设计

* [管理员](https://glossary.magento.com/admin) 用户帐户

* 访问控制列表(ACL)

## 媒体

本节将讨论如何手动迁移媒体文件。

### 存储在数据库中的媒体文件

>[!WARNING]
>
>数据库媒体存储方法自Magento2.4.3起被弃用。


本节适用于您 *仅* 如果将媒体文件存储在Magento数据库中。 此步骤应在 [数据迁移](data.md):

1. 以管理员身份登录到Magento1管理面板。

1. 单击 **系统** > **配置** >高级> **系统**.

1. 在右侧窗格中，滚动到 **介质的存储配置**.

1. 从 **选择媒体数据库** 列表，单击 [媒体存储](https://glossary.magento.com/media-storage) 数据库。

1. 单击 **同步**.

然后，在“Magento2管理员”面板中重复相同的步骤。

### 文件系统中的媒体文件

所有媒体文件(产品、类别、 [怀西威格](https://glossary.magento.com/wysiwyg) 编辑者等)应从 `<your Magento 1 install dir>/media` to `<your Magento 2 install dir>/pub/media`.

但是，请 *not* 复制 `.htaccess` 位于Magento1中的文件 `media` 文件夹。 Magento2有它自己的 `.htaccess` 应该保留。

## 店面设计

* 在文件(CSS、JS、模板、 [XML](https://glossary.magento.com/xml) 布局)更改了其位置和格式

* [布局](https://glossary.magento.com/layout) 数据库中存储的更新。 通过Magento1管理员 [CMS](https://glossary.magento.com/cms) 页面、CMS小组件、 [类别](https://glossary.magento.com/category) 页面和产品页面

## 访问控制列表(ACL)

您必须手动重新创建所有：

* Web服务API（SOAP、XML-RPC和REST）的凭据

* 管理用户帐户，将其与访问权限关联

>[!NOTE]
>
>您可以使用 `\Migration\Handler\Timezone` 处理程序。 请参阅 [随访](follow-up.md) 部分以了解更多详细信息。
