---
title: 付款處理與儲存的最佳實務
description: 瞭解如何安全地處理和儲存付款詳細資料
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 付款處理與儲存的最佳實務

維護的重要原則之一 [PCI法規遵循](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) 有適當處理和儲存信用卡付款的策略。

在Adobe Commerce中儲存持卡人資料是 **嚴禁** 這麼做可能會違反您身為商家的義務，違反支付卡產業資料安全標準(PCI-DSS)。 有關我們共同責任模式及商戶義務指引的更多資訊，請參閱我們的 [Adobe Commerce的共用責任指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 於Adobe信任中心。

我們建議您遵循下列最佳實務，以協助確保您正確處理電子商務網站上的付款資訊。 有關整體安全性最佳實務的其他指引，請參閱我們的 [Adobe Commerce安全性最佳實務指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) 在Adobe信任中心

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

* 雲端基礎結構上的Adobe Commerce
* Adobe Commerce內部部署

## 保護持卡人資料

如果需要儲存持卡人資料，則持卡人資料應透過儲存安全措施，儲存在Adobe Commerce外部。 針對信用卡持卡人資料等付款詳細資料制定儲存保障措施，有助於防止欺詐和其他潛在安全性問題。 與其他PCI標準一致，建立保護是第一道防線。 增強儲存資料保護的一些慣用方法包括加密、截斷、代碼化、單向雜湊和遮罩。

密碼編譯金鑰的保護對資料保護策略至關重要。 由技術高超且值得信賴的託管人來監管這些金鑰至關重要。

最後，主要帳號(PAN)在儲存期間必須無法讀取（例如，XXX等被遮罩）。 這包括可攜式儲存和備份媒體，例如快閃磁碟機、USB和外部硬碟，甚至稽核記錄。

## 加密持卡人資料的傳輸

在傳輸期間保護資料是保護付款資訊（例如持卡人資料）的關鍵。 當這些資訊透過開放網路傳輸時，可能會更容易受到安全性問題的攻擊。

### 使用安全傳輸通訊協定

使用安全的傳輸通訊協定和實務來傳輸持卡人資料，包括：

* 信任的金鑰和憑證
* TLS、SSH或VPN等安全傳輸通訊協定
* 加密中的非對稱演演算法
* 透過傳輸和顯示PAN進行Tokenization、遮罩和滲透測試
* 限制對持卡人資料的存取
* 敏感資訊的存取權應依需求知曉加以限制，並僅提供給具有業務需求的授權人員

處理持卡人資料的建議方法不是儲存主要帳號(PAN)，而是將信用卡與特定的付款處理提供者記號，並儲存代號、信用卡型別和加密的到期日。 您可以將權杖用作檔案上的認證，以供日後使用，因為此權杖僅供每個商家使用。 由於Token是唯一的，因此若發生安全性問題，Token就會失效，有助於防止詐騙活動

## 其他資訊

如果您正在尋找按Adobe列出的建議支付解決方案，請考慮 [Adobe付款服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
