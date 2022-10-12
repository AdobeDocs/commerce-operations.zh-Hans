---
title: 应用修补程序
description: 了解将修补程序应用到Adobe Commerce或Magento Open Source项目的方法。
source-git-commit: e2ddb30da8dd86236e1dcf33a3f911b67384a6d7
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# 应用修补程序

您可以使用以下任一方法应用修补程序：

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}
- [命令行](../patches/apply.md#command-line)
- [编辑器](../patches/apply.md#composer)

## 编辑器

>[!IMPORTANT]
>
>要应用正式的质量修补程序，请使用 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}。 在部署任何自定义修补程序之前，请务必先执行全面测试。

要使用编辑器应用自定义修补程序，请执行以下操作：

1. 打开命令行应用程序并导航到项目目录。
1. 添加 `cweagans/composer-patches` 插件 `composer.json` 文件。

   ```bash
   composer require cweagans/composer-patches
   ```

1. 编辑 `composer.json` 并添加以下部分以指定：
   - **模块：** *\&quot;magento/module-payment\&quot;*
   - **标题：** *\&quot;MAGETWO-56934:使用无效信用卡进行Authorize.net订购时，结帐页面冻结\&quot;*
   - **修补程序路径：** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

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

   如果修补程序影响多个模块，则必须创建多个针对多个模块的修补程序文件。

1. 应用修补程序。 使用 `-v` 选项。

   ```bash
   composer -v install
   ```

1. 更新 `composer.lock` 文件。 锁定文件跟踪对象中已将哪些修补程序应用于每个编辑器包。

   ```bash
   composer update --lock
   ```

## 命令行

要从命令行应用修补程序，请执行以下操作：

1. 将本地文件上传到 `<Magento_root>` 目录。
1. 以 [管理员用户](../../configuration/cli/config-cli.md#prerequisites) 并验证文件是否位于正确的目录中。
1. 在命令行界面中，根据修补程序扩展运行以下命令：

   ```bash
   patch < patch_file_name.patch
   ```

   该命令假定要修补的文件相对于修补程序文件的位置。

   >[!NOTE]
   >
   >如果命令行显示： `File to patch:`，则意味着即使路径正确，也无法找到目标文件。 在命令行终端中显示的框中，第一行显示要打补丁的文件。 复制文件路径，并将其粘贴到 `File to patch:` 提示和按 `Enter` 并且补丁应该完成。

1. 要反映更改，请在 **系统** >工具> **缓存管理**.

   或者，可以使用同一命令在本地应用修补程序，然后正常提交并推送。
