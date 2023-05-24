---
title: 需要手动迁移的数据
description: 了解在Magento1到Magento2数据迁移期间必须手动迁移的数据及其操作方法。
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '278'
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
>自Magento2.4.3起，数据库介质存储方法已弃用。


本节适用于您 *仅限* 在Magento数据库中存储介质文件。 此步骤应在之前执行 [数据迁移](data.md)：

1. 以管理员身份登录到Magento1管理面板。

1. 单击 **系统** > **配置** >高级> **系统**.

1. 在右窗格中，滚动到 **媒体的存储配置**.

1. 从 **选择媒体数据库** 列表中，单击媒体存储数据库的名称。

1. 单击 **同步**.

然后，在Magento2管理面板中重复相同的步骤。

### 文件系统中的媒体文件

所有媒体文件（产品、类别、 WYSIWYG编辑器等的图像）应手动从 `<your Magento 1 install dir>/media` 到 `<your Magento 2 install dir>/pub/media`.

但是，可以 *非* 复制 `.htaccess` Magento1中的文件 `media` 文件夹。 Magento2具有自己的 `.htaccess` 应该保留下来。

## 店面设计

* 文件（CSS、JS、模板、XML布局）中的设计更改了其位置和格式

* 布局更新存储在数据库中。 通过CMS页面、CMS小组件、类别页面和产品页面中的Magento1管理员放置

## 访问控制列表(ACL)

您必须手动重新创建所有：

* Web服务API（SOAP、XML-RPC和REST）的凭据

* 管理用户帐户并将其与访问权限相关联

>[!NOTE]
>
>您可以使用调整数据库实体的时区 `\Migration\Handler\Timezone` 处理程序。 请参阅 [后续活动](follow-up.md) 部分以了解更多详细信息。
