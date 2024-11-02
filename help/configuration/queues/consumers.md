---
title: 消息队列使用者
description: 了解Adobe Commerce消息队列使用者，包括与其关联的功能和系统配置设置。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# 消息队列使用者

下表标识了所有消息队列使用者，描述了他们的操作，并标识了与他们关联的管理员系统配置设置：

| 使用者和描述 | Adobe Commerce | 带有B2B的Adobe Commerce | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 为[批量操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)的每个单独任务创建消息，如导入或导出物料、批量更改价格以及将产品分配给仓库。 在管理员系统配置设置中将&#x200B;[**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations)选项设置为&#x200B;**[!UICONTROL Run asynchronously]**时需要。 |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| 在后台异步生成优惠券。 需要使用[批次优惠券生成](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons)功能。 |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| 检查已在Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/)的[Adobe I/O事件中注册为优先级的事件。 |
| `exportProcessor` | + | + | + |
| 防止在大型数据集（例如200,000个产品）的[导出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html)期间连接超时。 |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 在下达订单或移除产品后，异步更正股票指数。 在管理员配置设置中启用&#x200B;[**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options)选项时必需。 请参阅[性能最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update)。 |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 在删除产品时，按产品SKU异步删除源项目。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory)股票选项时必需。 |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| 异步处理旧库存物料、更新旧库存物料、更新默认来源物料和重新索引特定产品SKU的库存。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations)批量操作时需要。 |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 在删除产品后，按产品SKU异步删除预订。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory)股票选项时必需。 |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 在删除产品后，按产品SKU异步更新预留。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory)股票选项时必需。 |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 异步更新分配给库存的每种产品的可销售数量。 如果您使用[!DNL Inventory Management]，则此使用者应始终处于运行状态。 |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| 异步重新索引源项目。 在管理员系统配置设置中将&#x200B;[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)设置为“[!UICONTROL asynchronous]”时需要。 |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| 异步对股票进行重新索引。 在管理员系统配置设置中将&#x200B;[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)设置为“[!UICONTROL asynchronous]”时需要。 |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 创建临时数据库表，将每个[客户区段](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)移入其中，删除与区段ID匹配的所有区段，并使用区段ID作为指示符将它们复制到客户区段。 所有这些操作都在一个事务中完成，因此如果某个事务出现故障，它会将该事务回滚到执行该操作之前它原来的状态。 事务完成后，使用者删除临时表。 |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 确保将指向产品、类别、CMS块和CMS页面所分配媒体的链接正确分配给资产。 删除不再使用的旧资产。 |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| 生成并验证媒体资源路径。 资源的绝对路径由它在服务器上的媒体目录中的位置决定。 图像会调整大小（如有必要）并复制到生成的路径内的媒体目录中。 |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| 将图像文件导入到`media_gallery_asset`数据库表。 |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| 异步[调整](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images)目录图像的大小。 |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 更新可协商报价的价格。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes)选项时必需。 |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 异步[处理订单](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)，它将订单标记为已接收，将它们放入消息队列中，并以先进先出方式处理它们。 已考虑使用[最佳实践](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md)来改进可处理的订单数，因为客户无需等待后端流程完成即可看到成功消息。 |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 使用Admin进行更新[后，将更改异步写入数据库中的产品属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)。 |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 在使用Admin进行[更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)后，将更改异步写入数据库中特定商店视图的产品属性。 |                |                         |                     |
| `product_alert` | + | + | + |
| 向客户发送有关产品价格和库存变化的通知电子邮件。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html)选项时需要。 |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 将采购订单转换为[订单](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules)。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html)选项时必需。 |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 发送采购订单电子邮件。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html)选项时必需。 |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 根据相关[审批规则](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules)验证采购订单。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html)选项时必需。 |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 通过将保存作业置于消息队列中来异步保存存储配置更改，这可以提高包含大量存储级配置的部署的性能。 需要使用[`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save)模块。 |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| 避免出现可多次使用一次性优惠券的[问题](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html)。 |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 更新分配给共享目录类别的类别。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared)选项时必需。 |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 更新共享目录中每个产品的价格。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared)选项时必需。 |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 从目录中删除或从购物车中删除产品时，删除无效或不活动的报价。 在管理员系统配置设置中启用&#x200B;[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes)选项时必需。 |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 更新活动购物车以反映购物车价格规则中的更改。 更新&#x200B;[**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html)时需要此项。 |                |                         |                     |

{style="table-layout:auto"}
