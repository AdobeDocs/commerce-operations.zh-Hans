---
title: Security.txt
description: 瞭解如何提供資訊以協助安全性研究人員報告漏洞。
badge: label="Contributed by Kalpesh Mehta from Corra" type="Informational" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 安全性TXT檔案

當研究人員發現安全漏洞時，通常缺少適當的報告通道。 因此，系統不會回報某些漏洞。 目的 `security.txt` [檔案格式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) 檔案是用來向安全性研究人員提供他們可用來報告其發現的資訊。

商家可以輸入他們的聯絡資訊 [安全性問題報告](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) 來自Commerce _管理員_. 對於開發人員而言， `Magento_Securitytxt` 模組提供下列功能：

- 允許從儲存安全性設定 _管理員_.
- 包含路由器，以將要求的應用程式動作類別與 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 檔案。
- 提供以下專案的內容： `.well-known/security.txt` 和 `.well-known/security.txt.sig` 檔案。

有效的 `security.txt` 檔案可能如下所示：

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

若要建立 `security.txt` 簽名(`security.txt.sig`)檔案：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

若要驗證簽章：

```bash
gpg --verify security.txt.sig security.txt
```
