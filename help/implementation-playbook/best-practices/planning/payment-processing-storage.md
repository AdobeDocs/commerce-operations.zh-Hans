---
title: 支付处理和存储的最佳实践
description: 了解如何安全地处理和存储付款详细信息
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 124eaf6e7b465b320d3d7e6a3694130edb93f187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# 支付处理和存储的最佳实践

维护 [PCI合规性](https://nam04.safelinks.protection.outlook.com/GetUrlReputation) 正在制定策略，以正确处理和存储信用卡支付。

在Adobe Commerce中存储持卡人数据 **严禁** 而这样做可能违反您作为支付卡行业数据安全标准(PCI-DSS)下的商户的义务。 有关我们的商户责任分担模式和准则的更多信息，请参阅 [Adobe Commerce共享责任指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) Adobe信任中心。

我们建议遵循以下最佳实践，以帮助您正确处理电子商务网站上的付款信息。 有关整体安全最佳实践的其他指导，请参阅 [《Adobe Commerce安全最佳实践指南》](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) Adobe信任中心

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

* Adobe Commerce云基础架构
* Adobe Commerce内部

## 保护持卡人数据

如果需要存储持卡人数据，则持卡人数据应存储在Adobe Commerce外部，并提供存储保障。 为支付详细信息（如信用卡持卡人数据）设置存储保护，有助于防止欺诈和其他潜在安全问题。 与其他PCI标准相一致，保护到位是第一道防线。 增强存储数据保护的一些首选方法包括加密、截断、令牌化、单向哈希处理和掩码。

对加密密钥的保护对于数据保护策略至关重要。 拥有技能娴熟且值得信赖的托管机构来监督这些密钥至关重要。

最后，主帐号(PAN)在存储期间必须不可读（例如，XXX等被屏蔽）。 这包括可移植的存储和备份介质（如闪存驱动器、 USB和外置硬盘），甚至包括审核日志。

## 持卡人数据的加密传输

在传输过程中保护数据是保护支付信息（如持卡人数据）的关键。 当此信息通过开放网络传输时，它可能更容易受到安全问题的影响。

### 使用安全传输协议

使用安全传输协议和做法传输持卡人数据，包括：

* 受信任的密钥和证书
* 安全传输协议，如TLS、SSH或VPN
* 非对称加密算法
* 具有发射和显示PAN的Tokenizaton、掩蔽和渗透测试
* 限制对持卡人数据的访问
* 对敏感信息的访问应限制在知情需要的基础上，并仅提供给那些有业务需要的授权人员

处理持卡人数据的建议方法是，不存储主帐号(PAN)，而是与特定支付处理提供商对卡进行标记，并存储令牌、卡类型和加密的过期日期。 您可以将令牌用作文件上的凭据以供将来使用，因为令牌仅适用于每个商家。 由于令牌是唯一的，因此如果存在安全问题，则中的令牌将失效，这有助于防止欺诈活动

## 其他信息

如果您正在按Adobe查找推荐的支付解决方案，请考虑 [Adobe支付服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
