---
title: 檔案擁有權和許可權
description: 瞭解使用Adobe Commerce和Magento Open Source的內部安裝時，檔案系統許可權的重要性。
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 檔案擁有權和許可權

在開發環境中保護Adobe Commerce或Magento Open Source安裝安全，以協助防止未經授權人員或程式存取（並可能傷害）您的系統相關問題，這點很重要。 使用下列檔案系統擁有權和許可權准則來保護您的安裝。

## 檔案系統擁有者

檔案系統擁有者是擁有並保留檔案系統中檔案寫入許可權的使用者。

檔案系統擁有者有兩種型別：

- **與單一使用者共用託管**

   共用託管提供者可讓您以單一使用者身分登入應用程式伺服器。 您可以透過單一使用者身分登入、使用FTP傳輸檔案，以及執行網頁伺服器。 您可以選擇設定 [`umask`](#restrict-access-with-a-umask) 以進一步限制存取，尤其是在生產環境中。

- **由兩個使用者進行私人託管**

   如果您管理應用程式伺服器，私人託管會很有用。 每位使用者都有特定的職責：

   - 此 _網頁伺服器使用者_ 執行管理員和店面。

   - 此 _命令列使用者_ 執行cron作業和命令列公用程式。
   兩位使用者都需要相同的檔案系統許可權，因此最好使用 [共用群組](configure-permissions.md#set-ownership-and-permissions-for-two-users) 並設定 [`umask`](#restrict-access-with-a-umask).

### 使用umask限制存取

若要加強安全性，尤其是在共用託管系統的生產環境中，您可以使用 `umask` 以限制存取。 A `umask` — 也稱為 _檔案系統建立遮罩_ — 是一組位元，可控制如何為新建立的檔案設定檔案許可權。

>[!WARNING]
>
>檔案系統安全性既複雜又重要。 強烈建議您先洽詢經驗豐富的系統管理員或網路管理員，再決定要設定的許可權層級。 我們提供您可使用的機制，但建立許可權策略是您的責任。

Adobe Commerce和Magento Open Source使用三位元預設遮色片： `002`. 從UNIX預設值（檔案為666，目錄為777）中減去預設遮色片。

例如：

- **775用於目錄** — 由使用者完全控制、由群組完全控制，並讓每個人都能周遊目錄。 共用託管提供者通常需要這些許可權。

- **664 （檔案）** — 使用者可寫入、群組可寫入，其他所有人皆為唯讀。

如需有關建立 `magento_umask` 檔案，請參閱 [設定umask](../../next-steps/set-umask.md).

## 許可權、擁有權和應用程式模式

建議您在使用不同的Adobe Commerce和Magento Open Source應用程式模式時，使用不同的許可權和擁有權：

- 預設
- 開發人員
- 生產

另請參閱 [關於模式](../../../configuration/bootstrap/application-modes.md) 在 _設定指南_.

我們將在中進一步討論許可權建議 [檔案系統存取許可權](../../../configuration/deployment/file-system-permissions.md) 在 _設定指南_.

>[!TIP]
>
>安裝Adobe Commerce或Magento Open Source之前，請先檢閱 [設定檔案所有權與許可權](configure-permissions.md).
