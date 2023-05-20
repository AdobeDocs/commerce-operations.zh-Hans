---
title: 建立、編輯或解除鎖定管理員帳戶
description: 請依照下列步驟管理Adobe Commerce或Magento Open Source管理員應用程式的管理員帳戶。
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 建立、編輯或解除鎖定管理員帳戶

您必須先執行下列動作，才能使用此命令：

- [建立部署設定](deployment.md)
- [至少啟用Magento_Authorization和Magento_User模組](manage-modules.md)
- 建立資料庫綱要

>[!NOTE]
>
>建立資料庫最簡單的方法是使用指令 `magento setup:upgrade`.

## 建立或編輯管理員

使用此命令可建立管理員或編輯現有的管理員。

>[!NOTE]
>
>如果您正在編輯管理員，則僅 `first name`， `last name`、和 `password` 可以編輯。

命令使用方式：

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

下表定義引數和值：

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員使用者的名字。 | 是 |
| `--admin-lastname` | 管理員使用者的姓氏。 | 是 |
| `--admin-email` | 管理員使用者的電子郵件地址。 | 是 |
| `--admin-user` | 管理員使用者名稱。 | 是 |
| `--admin-password` | 管理員使用者密碼。 密碼長度必須至少為7個字元，且必須至少包含一個字母和數字字元。 <br><br>我們建議使用更長、更複雜的密碼。 如果密碼字串包含需要常值解譯的特殊字元（例如反斜線或空格），請以單引號將密碼括住。 | 是 |
| `--magento-init-params` | 新增至任何命令以自訂應用程式初始化引數<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |

使用範例：

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

如果您未指定任何必要引數，應用程式會在CLI中詢問相關引數：

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

以下範例更新 `first name`， `last name`、和 `password` 之 `j.doe` 管理員使用者：

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## 解除鎖定管理員帳戶

使用此命令可解除鎖定因多次錯誤登入嘗試而遭鎖定的管理員帳戶。

```bash
bin/magento admin:user:unlock {username}
```

您必須指定管理員的使用者名稱。 範例：

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

如果帳戶未解除鎖定或發生問題，則會顯示下列訊息：

```terminal
The user account "admin" was not locked or could not be unlocked
```

確認使用者是管理員、使用者處於作用中狀態，且帳戶已鎖定。 若要檢視「管理員」中鎖定的使用者清單，請以管理員身分登入，然後按一下 **系統** > **許可權** > **鎖定的使用者**.

如果帳戶不存在，則會顯示下列訊息：

```terminal
Couldn't find the user account "bob"
```
