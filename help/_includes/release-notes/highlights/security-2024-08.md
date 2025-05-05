---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# 2024年8月安全修补程序亮点

此版本包括以下功能亮点：

* **[!DNL one-time passwords]**&#x200B;的速率限制 — 以下新的系统配置选项现在可用于在[!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)]验证中启用速率限制：

   * 对双重身份验证进行&#x200B;[!UICONTROL **重试尝试限制**]
   * [!UICONTROL **双重身份验证锁定时间（秒）**]

  Adobe建议为2FA OTP验证设置阈值以限制重试尝试的次数，从而缓解暴力攻击。 有关详细信息，请参阅&#x200B;_配置参考指南_&#x200B;中的[安全性> 2FA](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/config/security/2fa)。<!-- AC-12095 -->

* **加密密钥轮替** — 现在可以使用新的CLI命令更改您的加密密钥。 有关详细信息，请参阅[Troubleshooting Encryption Key Rotation： CVE-2024-34102](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102)知识库文章。

* **修复[CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** — 解决了[!DNL Prototype.js]安全漏洞。<!-- AC-11936 -->

* **修复[CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)** — 解决远程代码执行安全漏洞。 此漏洞会影响使用Apache Web Server进行内部部署或自托管部署的商家。 此修复还作为独立修补程序提供。 有关详细信息，请参阅Adobe Commerce可用的[安全更新 — APSB24-61](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61)知识库文章。<!-- ACSD-60551 -->
