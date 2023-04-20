---
title: 消息队列使用者
description: 了解Adobe Commerce和Magento Open Source消息队列使用者，包括与他们关联的功能和系统配置设置。
source-git-commit: f9db986510a3ec8e62b9d628da40fdfd9741479f
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---


# 消息队列使用者

下表标识了所有消息队列使用者，描述了他们的工作，并标识了与他们关联的管理员系统配置设置：

| 消费者和描述 | Adobe Commerce | Adobe Commerce与B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 为 [批量操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)，例如导入或导出物料、大规模更改价格以及将产品分配到仓库。 在 [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) 选项设置为&#x200B;**[!UICONTROL Run asynchronously]**（在管理系统配置设置中）。 |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| 在后台异步生成优惠券。 使用 [批量优惠券生成](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 功能。 |  |  |  |
| `commerce.eventing.event.publish` | + | + |  |
| 检查已在中注册为优先级的事件 [Adobe I/OAdobe Commerce事件](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| 在 [导出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 大数据集（例如200,000个产品）。 |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| 下订单或删除产品后，异步更正股指。 在 [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) 选项。 请参阅 [性能最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| 删除产品后，会按产品SKU异步删除源项目。 在 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 在管理系统配置设置中启用了“库存”选项。 |  |  |  |
| `inventory.mass.update` | + | + | + |
| 异步处理旧版库存项目、更新旧版库存项目、更新默认源项目，以及为特定产品SKU重新编入库存索引。 在 [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 在管理系统配置设置中启用了批量操作。 |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| 删除产品后，按产品SKU异步删除保留。 在 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 在管理系统配置设置中启用了“库存”选项。 |  |  |  |
| `inventory.reservations.update` | + | + | + |
| 删除产品后，按产品SKU异步更新预订。 在 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 在管理系统配置设置中启用了“库存”选项。 |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 异步更新分配给库存的每个产品的可售数量。 如果您使用 [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| 异步重新索引源项。 在 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 设置为&quot;[!UICONTROL asynchronous]”。 |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| 异步重新索引股票。 在 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 设置为&quot;[!UICONTROL asynchronous]”。 |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| 创建临时数据库表，移动每个表 [客户区段](https://docs.magento.com/user-guide/marketing/customer-segments.html) 在中，删除与区段ID匹配的所有区段，并使用区段ID作为指示符，将其复制到客户区段。 这全部是在事务中完成的，因此如果某件事发生故障，它会将事务回滚到执行此操作前的状态。 交易后，用户将删除临时表。 |  |  |  |
| `media.content.synchronization` | + | + | + |
| 确保为资产正确分配产品、类别、CMS块和CMS页面的指向已分配媒体的链接。 删除不再使用的旧资产。 |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| 生成并验证媒体资产路径。 资产的绝对路径取决于资产在服务器上从媒体目录内部的位置。 图像会调整大小（如有必要），并复制到生成路径内的媒体目录中。 |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| 将图像文件导入到 `media_gallery_asset` 数据库表。 |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| 异步 [调整大小](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) 目录图像。 |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| 更新可转让报价的价格。 在 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 选项。 |  |  |  |
| `placeOrderProcessor` | + | + |  |
| 异步 [处理订单](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)，将订单标记为已接收，将其放入消息队列，并按先入先出的方式处理它们。 被视为 [最佳实践](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) ，因为客户在看到成功消息之前无需等待后端进程完成，因此可以处理更多订单。 |  |  |  |
| `product_action_attribute.update` | + | + | + |
| 使用管理员之后，将更改异步写入数据库中的产品属性 [进行更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| 使用管理员在 [进行更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| 向客户发送有关产品价格和库存更改的通知电子邮件。 当 [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 选项。 |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| 将采购订单转换为 [订购](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). 在 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 选项。 |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| 发送采购订单电子邮件。 在 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 选项。 |  |  |  |
| `purchaseorder.validation` |  | + |  |
| 根据相关验证采购订单 [批准规则](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). 在 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 选项。 |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| 阻止 [问题](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 可多次使用一次性优惠券。 |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| 更新分配给共享目录类别的类别。 在 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 选项。 |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| 更新共享目录中每个产品的价格。 在 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 选项。 |  |  |  |
| `quoteItemCleaner` | + | + |  |
| 从目录中删除产品或从购物车中删除产品时，删除无效或不活动的报价。 在 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 选项。 |  |  |  |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 更新活动购物车以反映购物车价格规则中的更改。 更新时需要 [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |  |  |  |

{style="table-layout:auto"}
