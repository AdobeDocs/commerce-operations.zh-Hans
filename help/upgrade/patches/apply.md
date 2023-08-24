---
title: 应用修补程序
description: 了解将修补程序应用于Adobe Commerce或Magento Open Source项目的方法。
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: 454f586737292341b3e6dd9a57cc92b3472c4b31
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 应用修补程序

可以使用以下任一方法应用修补程序：

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [命令行](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)


>[!TIP]
>
>请参阅 [最佳实践](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) 有关Adobe Commerce的企业级集中打补丁的信息。

## Composer

>[!IMPORTANT]
>
>要应用官方质量补丁，请使用 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 在部署任何自定义修补程序之前，请始终执行全面的测试。

要使用编辑器应用自定义修补程序，请执行以下操作：

1. 打开命令行应用程序并导航到项目目录。
1. 添加 `cweagans/composer-patches` 插件 `composer.json` 文件。

   ```bash
   composer require cweagans/composer-patches
   ```

1. 编辑 `composer.json` 并添加以下部分以指定：
   - **模块：** *\&quot;magento/module-payment\&quot;*
   - **标题：** *\&quot;MAGETWO-56934：使用Authorize.net订购信用卡无效时，结账页面冻结\&quot;*
   - **修补程序的路径：** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   例如：

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   如果修补程序影响多个模块，则必须创建针对多个模块的多个修补程序文件。

1. 应用修补程序。 使用 `-v` 选项。

   ```bash
   composer -v install
   ```

1. 更新 `composer.lock` 文件。 锁定文件会跟踪哪些修补程序已应用于对象中的每个Composer包。

   ```bash
   composer update --lock
   ```

## 命令行

要从命令行应用修补程序，请执行以下操作：

1. 将本地文件上传到 `<Magento_root>` FTP、SFTP、SSH或您普通的传输方法所在的服务器上的目录。
1. 以以下身份登录服务器 [管理员用户](../../configuration/cli/config-cli.md#prerequisites) 并验证文件是否在正确的目录中。
1. 在命令行界面中，根据修补程序扩展运行以下命令：

   ```bash
   patch < patch_file_name.patch
   ```

   该命令假定要打补丁的文件相对于打补丁文件。

   >[!NOTE]
   >
   >如果命令行显示： `File to patch:`，这意味着它找不到所需的文件，即使路径看起来是正确的。 在命令行终端中显示的框中，第一行显示要修补的文件。 复制文件路径并将其粘贴到 `File to patch:` 提示并按 `Enter` 修补程序应该已完成。

1. 要反映更改，请在下的管理员中刷新缓存 **系统** >工具> **缓存管理**.

   或者，也可以使用相同的命令在本地应用修补程序，然后正常提交和推送。
