---
title: 支付处理和存储的最佳实践
description: 了解如何安全地处理和存储付款详细信息
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 支付处理和存储的最佳实践

维护的关键原则之一 [PCI合规性](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) 正在制定适当处理和存储信用卡支付的策略。

在Adobe Commerce中存储持卡人数据是 **严格禁止** 这样做可能会违反您作为商家对支付卡行业数据安全标准(PCI-DSS)的义务。 有关我们共同责任模式及商户责任指引的更多信息，请参阅我们的 [Adobe Commerce的责任分担指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 在Adobe托管中心。

我们建议遵循以下最佳实践，以帮助确保正确处理电子商务网站上的付款信息。 有关整体安全最佳实践的其他指导，请参阅 [Adobe Commerce安全最佳实践指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) 在Adobe托管中心

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

* 云基础架构上的Adobe Commerce
* Adobe Commerce内部部署

## 保护持卡人数据

如果需要存储持卡人数据，则应将持卡人数据存储在Adobe Commerce外部，并具备存储保护功能。 为支付详细信息（如信用卡持卡人数据）提供存储保护，有助于防止欺诈和其他潜在安全问题。 与其他PCI标准一样，建立保护是第一道防线。 增强存储数据的保护的一些优选方法包括加密、截断、标记化、单向散列和掩蔽。

加密密钥的保护对于数据保护策略至关重要。 让技术熟练且值得信赖的托管人监管这些密钥，这一点至关重要。

最后，主帐号(PAN)在存储期间必须不可读（例如，被掩盖，如XXX）。 这包括便携式存储和备份介质，如闪存驱动器、 USB和外部硬盘，甚至审核日志。

## 加密持卡人数据的传输

在传输期间保护数据是保护支付信息（如持卡人数据）的关键。 当这些信息通过开放网络传输时，它可能会更容易受到安全问题的攻击。

### 使用安全传输协议

使用安全传输协议和实践传输持卡人数据，包括：

* 受信任的密钥和证书
* 安全传输协议，如TLS、SSH或VPN
* 加密中的非对称算法
* 通过传输和显示PAN进行令牌化、掩蔽和渗透测试
* 限制对持卡人数据的访问
* 应根据知情需要限制对敏感信息的访问，并且仅允许具有业务需要的授权人员访问

处理持卡人数据的推荐方法是不存储主帐号(PAN)，而是将卡与特定的支付处理提供商进行标记，并存储标记、卡类型和加密的到期日期。 您可以将该令牌用作文件的凭据，以供将来使用，因为它仅对每个商家是唯一的。 由于令牌是唯一的，因此如果存在安全问题，则中的令牌会失效，这有助于防止欺诈活动

## 其他信息

如果您在寻找按Adobe划分的推荐支付解决方案，请考虑 [Adobe支付服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
