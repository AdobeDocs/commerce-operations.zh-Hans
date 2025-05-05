---
title: Security.txt
description: 了解如何提供信息以帮助安全研究人员报告漏洞。
feature: Configuration, Security
badge: label="由卡尔佩什·梅赫塔从科拉市撰写" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="卡尔佩什梅赫塔"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# 安全TXT文件

当研究人员发现安全漏洞时，往往缺乏适当的报告渠道。 因此，某些漏洞未报告。 `security.txt` [文件格式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09)文件的目的是为安全研究人员提供可用于报告其发现的信息。

商家可以从Commerce _管理员_&#x200B;输入[安全问题报告](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/security-issue-reporting)的联系信息。 对于开发人员，`Magento_Securitytxt`模块提供了以下功能：

- 允许从&#x200B;_管理员_&#x200B;保存安全配置。
- 包含将应用程序操作类与`.well-known/security.txt`和`.well-known/security.txt.sig`文件的请求匹配的路由器。
- 提供`.well-known/security.txt`和`.well-known/security.txt.sig`文件的内容。

有效的`security.txt`文件可能如下所示：

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

要创建`security.txt`签名(`security.txt.sig`)文件：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

验证签名：

```bash
gpg --verify security.txt.sig security.txt
```
