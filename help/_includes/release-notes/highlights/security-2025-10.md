---
source-git-commit: e87b8a085c69d556b7fd0e341f073e363d5fa2e9
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---
# 2025年10月安全修补程序要点

此版本包括对CVE-2025-54236的修复，可解决REST API漏洞。

Adobe于2025年9月发布了针对此问题的修补程序。 有关详细信息，请参阅[所需操作：可用于Adobe Commerce的关键安全更新(APSB25-88)](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27397)知识库文章。<!-- AC-15379 -->

开发人员必须审查[REST API构造函数参数验证](https://developer.adobe.com/commerce/php/development/components/web-api/services/#rest-api-constructor-parameter-validation)，以了解如何更新扩展以符合这些安全更改。
