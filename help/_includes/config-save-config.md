---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 更新共享配置

**更新配置**:

1. 以文件系统所有者的身份登录到开发系统，或切换到。

1. 更改为应用程序根并运行dump命令。

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例如，如果Commerce安装在 `/var/www/html/magento2`，输入：

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. 确认 `app/etc/config.php` 已更新。

   ```bash
   git status
   ```

   示例响应：

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >做 _not_ 将更改提交到 `generated`, `pub/media`或 `pub/static` 目录到源代码管理。 在生成系统上生成这些文件。 开发系统可能具有代码、主题等，这些代码、主题等尚未准备好在生产系统上使用。

1. 签入对 `app/etc/config.php` 仅发送至源控件。

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
