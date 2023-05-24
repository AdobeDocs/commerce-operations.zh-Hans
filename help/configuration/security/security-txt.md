---
title: Security.txt
description: 了解如何提供信息以帮助安全研究人员报告漏洞。
feature: Configuration, Security
badge: label="由Kalpesh Mehta from Corra" type="Informational" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"提供
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 安全TXT文件

当研究人员发现安全漏洞时，往往缺乏适当的报告渠道。 因此，不会报告某些漏洞。 目的 `security.txt` [文件格式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) file是为安全研究人员提供可以用来报告其发现的信息。

商家可以输入他们的联系信息 [安全问题报告](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) 来自Commerce _管理员_. 对于开发人员， `Magento_Securitytxt` 模块提供以下功能：

- 允许从保存安全配置 _管理员_.
- 包含路由器，用于将请求的应用程序操作类与 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 文件。
- 提供 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 文件。

有效 `security.txt` 文件可能如下所示：

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

要创建 `security.txt` 签名(`security.txt.sig`)文件：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

验证签名：

```bash
gpg --verify security.txt.sig security.txt
```
