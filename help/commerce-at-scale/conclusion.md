---
title: 結論
description: 重新造訪大規模提供Commerce體驗指南中的概念。
exl-id: a5d5c398-451f-4283-b787-d16c7486e824
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# 結論

本內容旨在作為高層級指南，在準備AEM/CIF/Adobe Commerce環境以承受高負載時提供一些要初步調查的區域。 上述指南未涵蓋Adobe Commerce、CIF和Fastly的許多領域，這些領域需要針對您的環境進行最佳化。 此外，自訂程式碼和協力廠商模組可能會影響回應時間，此處不提供相關說明。

為了降低引入會對AEM/CIF/Adobe Commerce一般使用者回應時間產生負面影響的變更或程式碼的風險，應確保實施徹底且可重複的效能測試策略，包括定義可隨時間測量的KPI。 效能測試不僅應在上線前執行，也應在上線後繼續，最好是在每個主要版本或生產環境的變更前執行，以測量任何效能影響。
