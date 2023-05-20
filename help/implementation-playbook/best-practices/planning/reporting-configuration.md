---
title: 報告設定的最佳實務
description: 如果您未使用報表模組，請移除報表模組以最佳化網站效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# 報告設定的最佳實務

如果您的企業不需要報告或動態客戶區段功能，請停用 [報表功能](https://docs.magento.com/user-guide/configuration/general/reports.html) 以提升商店效能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 停用報告

如果您未使用報表或動態客戶區段，請停用「報表」功能。

1. 在管理員中，瀏覽至 **商店** > **設定** > **設定** > **一般** > **報表**.
1. 下 **一般選項**，設定 **啟用報表** 至 *否*.
1. 執行以排清快取 `php bin/magento cache:flush` 或在「管理員」中的 **系統** > **工具** > **快取管理**.

## 其他資訊

- [在Adobe Commerce中產生報表](https://docs.magento.com/user-guide/reports.html)
- [客戶動態區段](https://docs.magento.com/user-guide/marketing/customer-segments.html)
