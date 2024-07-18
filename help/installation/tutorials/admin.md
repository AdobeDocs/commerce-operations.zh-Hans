---
title: 创建、编辑或解锁管理员帐户
description: 按照以下步骤管理Adobe Commerce Admin应用程序的管理员帐户。
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 创建、编辑或解锁管理员帐户

在使用此命令之前，必须执行以下操作：

- [创建部署配置](deployment.md)
- [至少启用Magento_授权和Magento_用户模块](manage-modules.md)
- 创建数据库模式

>[!NOTE]
>
>创建数据库的最简单方法是使用命令`magento setup:upgrade`。

## 创建或编辑管理员

使用此命令可创建管理员或编辑现有管理员。

>[!NOTE]
>
>如果您正在编辑管理员，则只能编辑`first name`、`last name`和`password`。

命令用法：

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

其中下表定义了参数和值：

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--admin-firstname` | 管理员用户的名字。 | 是 |
| `--admin-lastname` | 管理员用户的姓氏。 | 是 |
| `--admin-email` | 管理员用户的电子邮件地址。 | 是 |
| `--admin-user` | 管理员用户名。 | 是 |
| `--admin-password` | 管理员用户密码。 密码长度必须至少为7个字符，并且必须至少包含一个字母和至少一个数字字符。 <br><br>我们建议使用更长、更复杂的密码。 如果密码字符串包含需要文字解释的特殊字符（如反斜杠或空格），请用单引号将密码括起来。 | 是 |
| `--magento-init-params` | 添加到任何命令以自定义应用程序初始化参数<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |

使用示例：

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

如果未指定任何必需的参数，应用程序会在CLI中询问这些参数：

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

以下示例更新了`j.doe`管理员用户的`first name`、`last name`和`password`：

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## 解锁管理员帐户

使用此命令可解锁通常由于多次错误登录尝试而锁定的管理员帐户。

```bash
bin/magento admin:user:unlock {username}
```

必须指定管理员的用户名。 示例：

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

如果帐户未解锁或出现问题，则会显示以下消息：

```
The user account "admin" was not locked or could not be unlocked
```

验证用户是否为管理员、用户是否处于活动状态以及帐户是否已锁定。 要查看管理员中锁定的用户列表，请以管理员身份登录，然后单击&#x200B;**系统** > **权限** > **锁定的用户**。

如果帐户不存在，则会显示以下消息：

```
Couldn't find the user account "bob"
```
