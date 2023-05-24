---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# 更新生成系统

**更新生成系统**：

1. 以文件系统所有者的身份登录到构建系统。
1. 切换到应用程序根目录。

   ```bash
   cd <Magento root dir>
   ```

1. 将更改提取到 `app/etc/config.php` 源代码管理中的。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 编译代码。

   ```bash
   bin/magento setup:di:compile
   ```

1. 编译代码后，生成静态视图文件。

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. 将更改签入源代码管理。

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
