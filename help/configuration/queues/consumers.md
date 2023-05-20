---
title: 訊息佇列消費者
description: 瞭解Adobe Commerce和Magento Open Source訊息佇列使用者，包括與其關聯的功能和系統組態設定。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---

# 訊息佇列消費者

下表會識別所有訊息佇列使用者、描述他們的工作，以及識別與其相關聯的管理系統組態設定：

| 消費者和說明 | Adobe Commerce | Adobe Commerce與B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 為的每項個別任務建立訊息 [大量作業](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)，例如匯入或匯出料號、大量變更價格，以及將產品指定至倉庫。 下列情況下需要 [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) 選項已設定為&#x200B;**[!UICONTROL Run asynchronously]**在管理系統組態設定中。 |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| 非同步地在背景產生抵用券。 使用 [批次優惠券產生](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 功能。 |  |  |  |
| `commerce.eventing.event.publish` | + | + |  |
| 檢查中是否已註冊為優先順序的事件 [Adobe Commerce的Adobe I/O事件](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| 防止連線逾時 [匯出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 大型資料集（例如200,000種產品）的數量。 |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| 在下達訂單或移除產品後，以非同步方式修正股票指數。 下列情況下需要 [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) 選項已啟用。 另請參閱 [效能最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| 移除產品時，會依產品SKU非同步刪除來源專案。 下列情況下需要 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 系統組態設定中的stock選項已啟用。 |  |  |  |
| `inventory.mass.update` | + | + | + |
| 非同步處理舊庫存料號、更新舊庫存料號、更新預設來源料號，以及重新索引特定產品SKU的存貨。 下列情況下需要 [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 大量作業在管理系統組態設定中啟用。 |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| 移除產品後，以非同步方式按產品SKU刪除預訂。 下列情況下需要 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 系統組態設定中的stock選項已啟用。 |  |  |  |
| `inventory.reservations.update` | + | + | + |
| 移除產品後，以非同步方式依產品SKU更新預訂。 下列情況下需要 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 系統組態設定中的stock選項已啟用。 |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 非同步更新指派給庫存的每種產品的可銷售數量。 如果您使用，此消費者應一律正常運作 [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| 以非同步方式重新索引來源專案。 下列情況下需要 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 設為&quot;[!UICONTROL asynchronous]&quot; （在管理系統組態設定中）。 |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| 以非同步方式重新索引股票。 下列情況下需要 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 設為&quot;[!UICONTROL asynchronous]&quot; （在管理系統組態設定中）。 |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| 建立暫存資料庫表格，移動每個 [客戶區段](https://docs.magento.com/user-guide/marketing/customer-segments.html) 在其中，刪除與區段ID相符的所有區段，並使用區段ID作為指標將其複製到客戶區段。 這全部是在交易中完成的，因此如果某個專案失敗，就會將交易復原到執行此動作之前的狀態。 交易後，消費者會捨棄臨時表格。 |  |  |  |
| `media.content.synchronization` | + | + | + |
| 確保將產品、類別、CMS區塊和CMS頁面的指派媒體連結正確指派給資產。 移除不再使用的舊資產。 |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| 產生並驗證媒體資產路徑。 資產的絕對路徑取決於它從媒體目錄內位於伺服器上的位置。 影像會重新調整大小（如有必要）並複製到產生路徑內的媒體目錄中。 |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| 將影像檔案匯入 `media_gallery_asset` 資料庫表格。 |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同步 [調整大小](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) 目錄影像。 |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| 更新可轉讓報價的價格。 下列情況下需要 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 選項。 |  |  |  |
| `placeOrderProcessor` | + | + |  |
| 非同步 [處理訂單](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)，會將訂單標示為已接收、將訂單放入訊息佇列中，並以先入先出方式處理。 視為 [最佳實務](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) 改善可處理的訂單數量，因為客戶不需要等待後端程式完成再看到成功訊息。 |  |  |  |
| `product_action_attribute.update` | + | + | + |
| 使用管理員後，以非同步方式將變更寫入資料庫中的產品屬性 [進行更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| 使用管理員後，以非同步方式將變更寫入資料庫中特定商店檢視的產品屬性 [進行更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| 傳送通知電子郵件給客戶，告知產品價格和存貨變更。 在以下情況下為必要： [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 選項。 |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| 將採購單轉換為 [訂購](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). 下列情況下需要 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| 傳送採購單電子郵件。 下列情況下需要 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `purchaseorder.validation` |  | + |  |
| 根據相關驗證採購單 [核准規則](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). 下列情況下需要 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| 防止 [問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 其中單次使用抵用券可以多次使用。 |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| 更新指派給共用目錄類別的類別。 下列情況下需要 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 選項。 |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| 更新共用目錄中每個產品的價格。 下列情況下需要 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 選項。 |  |  |  |
| `quoteItemCleaner` | + | + |  |
| 從目錄中刪除或從購物車中移除產品時，會刪除無效或無效的報價單。 下列情況下需要 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 選項。 |  |  |  |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 更新使用中的購物車以反映購物車價格規則中的變更。 更新時需要使用 [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |  |  |  |

{style="table-layout:auto"}
