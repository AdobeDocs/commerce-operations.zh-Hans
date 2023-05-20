---
title: 使用環境變數的範例
description: 請參閱如何使用環境變數在開發系統中設定共用、系統專屬和敏感值的範例。
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---

# 使用環境變數的範例

此範例說明如何在開發系統中設定共用、系統專屬和敏感的值，然後使用共用設定的組合來設定生產系統中的所有值。 `config.php`和PHP環境變數。

這些組態設定可在開發系統和生產系統之間共用：

起始VAT編號與商店名稱 **商店** >設定> **設定** >一般> **一般**

這些組態設定是系統專屬的或敏感的，如下所述：

- 將電子郵件傳送至（敏感） **商店** >設定> **設定** >一般> **連絡人**
- 來自的預設電子郵件網域（系統特定） **商店** >設定> **設定** >客戶> **客戶設定** > **建立新帳戶選項**

您可以使用相同的程式來設定下列參照中的任何設定：

- [敏感和系統專屬設定路徑參考](../reference/config-reference-sens.md)
- [付款設定路徑參考](../reference/config-reference-payment.md)
- [一般設定路徑參考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴充功能設定路徑參考](../reference/config-reference-b2b.md)

## 開始之前

開始之前，請設定檔案系統許可權和擁有權，如中所述 [開發、建置和生產系統的先決條件](../deployment/prerequisites.md).

## 假設

本主題提供修改生產系統設定的範例。 您可以視需要選擇不同的設定選項。

在本範例中，我們假設如下：

- 您使用Git原始檔控制
- 開發系統可在名為的Git遠端存放庫中取得 `mconfig`
- 您的Git工作分支已命名 `m2.2_deploy`

## 步驟1：在開發系統中設定設定

若要在開發系統中設定預設地區設定和重量單位：

1. 登入管理員。
1. 按一下 **商店** >設定> **設定** >一般> **一般**.
1. 如果您有多個可用網站，請使用 **存放區檢視** 清單位於左上角，可切換至不同的網站，如下圖所示。

   ![切換網站](../../assets/configuration/split-deploy-switch-website.png)

1. 在右窗格中，展開 **存放區資訊**.
1. 如有必要，請清除 **使用預設值** 核取方塊旁的 **VAT編號** 欄位。
1. 在欄位中輸入數字(例如， `12345`)。
1. 在 **存放區名稱** 欄位，輸入值(例如 `My Store`)。
1. 按一下 **儲存設定**.
1. 使用 **存放區檢視** 清單以選取 **預設設定** 如下圖所示。

   ![切換到預設設定](../../assets/configuration/split-deploy-default-config.png)

1. 在左側導覽列的「一般」底下，按一下 **連絡人**.
1. 清除 **使用預設值** 核取方塊旁的 **傳送電子郵件至** 欄位。
1. 在欄位中輸入電子郵件地址。
1. 按一下 **儲存設定**.
1. 在左窗格中，按一下客戶> **客戶設定**.
1. 在右窗格中，展開 **建立新帳戶選項**.
1. 清除 **使用系統值** 核取方塊旁的 **預設電子郵件網域** 欄位。
1. 在欄位中輸入網域名稱。
1. 按一下 **儲存設定**.
1. 如果出現提示，請排清快取。

## 步驟2：更新設定

現在您已變更「管理員」中的設定，請將共用設定寫入檔案（如本節所述）。

{{$include /help/_includes/config-save-config.md}}

請注意，即使 `app/etc/env.php` （系統特定設定）已更新，請勿將其簽入原始檔控制。 稍後在本程式中，您將在生產系統上建立相同的組態設定。

## 步驟3：更新您的建置系統並產生檔案

現在您已確認將共用設定的變更提交至原始檔控制，您可以在建置系統中提取這些變更、編譯程式碼，並產生靜態檔案。 最後一個步驟是將這些變更提取至您的生產系統。

{{$include /help/_includes/config-update-build-system.md}}

## 步驟4：更新生產系統

該流程的最後一步是更新您的生產系統。 您必須分成兩個部分來執行：

- 更新敏感和系統專屬設定
- 更新共用設定

### 更新敏感和系統專屬設定

若要使用環境變數來設定敏感和系統專屬的設定，您必須知道以下內容：

- 每個設定的範圍

   如果您依照步驟1的指示進行，「傳送電子郵件至」的範圍為全域（亦即「預設設定」範圍），「預設電子郵件網域」的範圍為網站。

   您必須知道網站的程式碼，才能設定預設電子郵件網域設定值。 另請參閱 [使用環境變數來覆寫組態設定](../reference/override-config-settings.md#environment-variables) 以取得關於尋找它的詳細資訊。

- 每個設定的設定路徑

   此範例中使用的設定路徑如下：

   | 設定名稱 | 設定路徑 |
   |--------------|--------------|
   | 傳送電子郵件至 | `contact/email/recipient_email` |
   | 預設電子郵件網域 | `customer/create_account/email_domain` |

   您可以在以下位置找到所有敏感和系統特定的設定路徑： [敏感和系統專屬設定路徑參考](../reference/config-reference-sens.md).

#### 將設定路徑轉換為變數名稱

如中所述 [使用環境變數來覆寫組態設定](../reference/override-config-settings.md#environment-variables)，變數的格式為：

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

的值 `<SCOPE>` 是 `CONFIG__DEFAULT__` 全域範圍或 `CONFIG__WEBSITES__<WEBSITE CODE>` 用於網站範圍。

若要尋找 `<SYSTEM__VARIABLE__NAME>`，取代每個 `/` 字元（在設定路徑中具有兩個底線）。

變數名稱如下：

| 名稱 | 設定路徑 | 變數名稱 |
|--------------|--------------|--------------|
| 傳送電子郵件至 | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| 預設電子郵件網域 | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>上表有一個範例網站程式碼： `BASE`，作為預設電子郵件網域組態設定。 Replace `BASE` 搭配您商店的適當網站程式碼。

#### 使用環境變數設定變數

您可以在中設定變數值 `index.php` 使用下列格式：

```php
$_ENV['VARIABLE'] = 'value';
```

**若要設定變數值**：

1. 以檔案系統擁有者的身分登入生產系統，或切換至該擁有者。
1. 開啟 `<Commerce root dir>/pub/index.php` 在文字編輯器中。
1. 任何位置 `index.php`，請為變數設定類似下列的值：

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. 將變更儲存至 `pub/index.php` 並退出文字編輯器。
1. 繼續下一節。

### 更新共用設定

本節說明如何提取您在開發和建置系統上所做的所有變更，這些變更會更新共用組態設定（商店名稱和VAT編號）。

{{$include /help/_includes/config-update-prod-system.md}}

### 驗證Admin中的組態設定

本節探討如何在生產系統管理員中驗證組態設定。

**驗證組態設定的方式**：

1. 登入生產系統的管理員。
1. 按一下 **商店** >設定> **設定** >一般> **一般**.
1. 使用 **存放區檢視** 清單位於左上角，可切換至其他網站。

   您在開發系統中設定的共用組態選項顯示如下。

   ![檢查生產系統中的設定](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >此 **存放區名稱** 欄位在網站範圍中可編輯，但如果您切換至預設設定範圍，則無法編輯。 這是您在開發系統中設定選項的結果。 的值 **VAT編號** 在網站範圍中不可編輯。

1. 如果您尚未這樣做，請切換至預設設定範圍。
1. 在左側導覽列的「一般」底下，按一下 **連絡人**.

   此 **傳送電子郵件至** 欄位不可編輯，如下圖所示。 此為敏感設定。

   ![檢查生產系統中的設定](../../assets/configuration/split-deploy-verify-contacts.png)

1. 在左窗格中，按一下客戶> **客戶設定**.
1. 在右窗格中，展開 **建立新帳戶選項**.

   的值 **預設電子郵件網域** 欄位顯示如下。 這是系統專屬的設定。

   ![檢查生產系統中的設定](../../assets/configuration/split-default-domain.png)
