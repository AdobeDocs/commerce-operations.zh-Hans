---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 更新共享配置

**要更新配置**：

1. 以文件系统所有者的身份登录开发系统，或切换到文件系统所有者。

1. 更改为应用程序根并运行dump命令。

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例如，如果`/var/www/html/magento2`中安装了Commerce，请输入：

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. 确认`app/etc/config.php`已更新。

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
   >请&#x200B;_不_&#x200B;将对`generated`、`pub/media`或`pub/static`目录的更改提交到源代码管理。 您可以在生成系统上生成这些文件。 开发系统可能具有代码、主题等，尚未准备好用于生产系统。

1. 仅将您对`app/etc/config.php`的更改签入到源代码管理。

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
