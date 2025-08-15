---
title: 需要手动迁移的数据
description: 了解在将Magento 1数据迁移到Magento 2的过程中必须手动迁移的数据以及如何这样做。
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# 需要手动迁移的数据

有四种数据需要手动迁移：

* 媒体

* 店面设计

* 管理员用户帐户

* 访问控制列表(ACL)

## 媒体

本节讨论如何手动迁移介质文件。

### 存储在数据库中的媒体文件

>[!WARNING]
>
>自Magento 2.4.3起，数据库媒体存储方法已弃用。


如果您将媒体文件存储在Magento数据库中，则此部分仅适用于您&#x200B;**。 此步骤应在[迁移数据](data.md)之前执行：

1. 以管理员身份登录到Magento 1管理面板。

1. 单击&#x200B;**系统** > **配置** >高级> **系统**。

1. 在右窗格中，滚动到&#x200B;**Media的存储配置**。

1. 从&#x200B;**选择媒体数据库**&#x200B;列表中，单击媒体存储数据库的名称。

1. 单击&#x200B;**同步**。

然后，在Magento 2管理面板中重复相同的步骤。

### 文件系统中的媒体文件

所有媒体文件(产品、类别、WYSIWYG编辑器等的图像)都应从`<your Magento 1 install dir>/media`手动复制到`<your Magento 2 install dir>/pub/media`。

但是，请&#x200B;*不*&#x200B;复制Magento 1 `.htaccess`文件夹中的`media`文件。 Magento 2具有其自身的`.htaccess`，应当保留。

## 店面设计

* 文件（CSS、JS、模板、XML布局）中的设计更改了其位置和格式

* 布局更新存储在数据库中。 通过Magento 1管理员放置在CMS页面、CMS小组件、类别页面和产品页面中

## 访问控制列表(ACL)

您必须手动重新创建所有：

* web服务API(SOAP、XML-RPC和REST)的凭据

* 管理用户帐户并将其与访问权限关联

>[!NOTE]
>
>您可以使用`\Migration\Handler\Timezone`处理程序调整数据库实体的时区。 有关更多详细信息，请参阅[跟进](follow-up.md)部分。
