---
title: 安装扩展
description: 按照以下步骤安装Adobe Commerce扩展。
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# 安装扩展

扩展或自定义Adobe Commerce行为的代码称为扩展。 您可以选择在上打包和分发扩展 [Commerce Marketplace](https://marketplace.magento.com) 或者另一个扩展分发系统。

扩展包括：

- 模块(扩展Adobe Commerce功能)
- 主题（更改店面和管理员的外观）
- 语言包（将店面和管理员本地化）

>[!TIP]
>
>本主题介绍如何使用命令行安装您从Commerce Marketplace购买的扩展。 您可以使用相同的过程来安装 _任意_ 扩展；您只需要扩展的编辑器名称和版本。 要找到它，请打开扩展的 `composer.json` 文件并记下 `"name"` 和 `"version"`.

安装之前，您可能需要：

1. 备份数据库。
1. 启用维护模式：

   ```bash
   bin/magento maintenance:enable
   ```

要安装扩展，您必须：

1. 从Commerce Marketplace或其他扩展开发人员处获取扩展。
1. 如果从Commerce Marketplace安装扩展，请确保 `repo.magento.com` 存储库存在于您的 `composer.json` 文件：

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. 获取扩展的编辑器名称和版本。
1. 更新 `composer.json` 使用扩展名的名称和版本创建文件。
1. 验证扩展是否已正确安装。
1. 启用并配置该扩展。

## 获取扩展编辑器名称和版本

如果您已经知道扩展的编辑器名称和版本，请跳过此步骤并继续操作 [更新您的 `composer.json` 文件](#update-your-composer-file).

要从Commerce Marketplace中获取扩展的编辑器名称和版本，请执行以下操作：

1. 登录 [Commerce Marketplace](https://marketplace.magento.com) 以及购买扩展时所用的用户名和密码。

1. 在右上角，单击 **您的姓名** > **我的个人资料**.

   ![访问您的Marketplace帐户](../../assets/installation/marketplace-my-profile.png)

1. 单击 **我的购买**.

   ![Marketplace购买历史记录](../../assets/installation//marketplace-my-purchases.png)

1. 找到要安装的扩展，然后单击 **技术详细信息**.

   ![技术详细信息显示扩展的编辑器名称](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>或者，您也可以找到的“编辑器”名称和版本 _任意_ 扩展(无论您是在Commerce Marketplace上还是在其他位置购买的) `composer.json` 文件。

## 更新您的编辑器文件

将扩展的名称和版本添加到 `composer.json` 文件：

1. 导航到项目目录并更新您的 `composer.json` 文件。

   ```bash
   composer require <component-name>:<version>
   ```

   例如，

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. 输入您的 [身份验证密钥](../prerequisites/authentication-keys.md). 您的公钥是您的用户名；您的私钥是您的密码。

1. 等待Composer完成项目依赖项的更新，并确保没有任何错误：

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## 验证扩展

要验证扩展是否正确安装，请运行以下命令：

```bash
bin/magento module:status J2t_Payplug
```

默认情况下，该扩展可能已禁用：

```terminal
Module is disabled
```

扩展名采用格式 `<VendorName>_<ComponentName>`；这与编辑器名称格式不同。 使用此格式启用扩展。 如果不确定扩展名称，请运行：

```bash
bin/magento module:status
```

并在“已禁用的模块列表”下查找扩展。

## 启用扩展

除非先清除生成的静态视图文件，否则某些扩展无法正常工作。 使用 `--clear-static-content` 启用扩展时用于清除静态视图文件的选项。

1. 启用扩展并清除静态视图文件：

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   您应该会看到以下输出：

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. 注册扩展：

   ```bash
   bin/magento setup:upgrade
   ```

1. 重新编译项目：在生产模式下，您可能会收到一条消息“请重新运行Magento编译命令”。 应用程序不会提示您以开发人员模式运行compile命令。

   ```bash
   bin/magento setup:di:compile
   ```

1. 验证扩展是否已启用：

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   您应该会看到验证扩展是否已不再禁用的输出：

   ```terminal
   Module is enabled
   ```

1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 根据需要在Admin中配置该扩展。

>[!TIP]
>
>如果在浏览器中加载店面时遇到错误，请使用以下命令清除缓存： `bin/magento cache:flush`.

## 升级扩展

要更新或升级模块或扩展，请执行以下操作：

1. 从Marketplace或其他扩展开发人员下载更新的文件。 记下模块名称和版本。

1. 将内容导出到应用程序根目录。

1. 如果模块存在编辑器包，请运行以下任一操作。

   每个模块名称更新：

   ```bash
   composer update vendor/module-name
   ```

   每个版本更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 运行以下命令以升级、部署和清理缓存。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
