---
title: 部署先决条件
description: 请参阅将Commerce部署到开发、构建或生产系统的先决条件列表。
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# 开发、构建和生产系统的先决条件

文件权限和所有权在开发、构建和生产系统中必须保持一致。 要使此功能正常工作，您必须：

- 以下所有项：

   - 在所有系统上设置相同的文件系统所有者用户名
   - 确保Web服务器在所有系统上都以相同用户身份运行
   - 确保文件系统所有者在所有系统上的Web服务器组中

- 根据需要使用以下准则更改每个系统上的Commerce文件系统权限和所有权：

   - 开发和构建： [设置安装前的所有权和权限（两个用户）](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - 生产： [开发和生产中的商业所有权和权限](file-system-permissions.md)

>[!INFO]
>
>如果选择此方法，则每次从构建系统提取代码时（如果构建系统中的文件系统所有者或Web服务器用户不同），都必须设置文件系统权限和所有权。
