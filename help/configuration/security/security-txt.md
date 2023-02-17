---
title: Security.txt
description: 了解如何提供信息以帮助安全研究人员报告漏洞。
badge: label="Kalpesh Mehta从Corra提供" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# 安全TXT文件

当研究人员发现安全漏洞时，往往缺乏适当的报告渠道。 因此，不报告某些漏洞。 的目的 `security.txt` [文件格式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) 文件是为安全研究人员提供他们可用于报告其调查结果的信息。

商户可以输入其联系信息 [安全问题报告](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) 从商务 _管理员_. 对于开发人员， `Magento_Securitytxt` 模块提供了以下功能：

- 允许从 _管理员_.
- 包含一台路由器，用于匹配 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 文件。
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

创建 `security.txt` 签名(`security.txt.sig`)文件：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

要验证签名，请执行以下操作：

```bash
gpg --verify security.txt.sig security.txt
```
