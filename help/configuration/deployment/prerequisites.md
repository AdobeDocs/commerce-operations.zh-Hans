---
title: 部署先决条件
description: 请参阅将商务部署到开发、构建或生产系统的先决条件列表。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 开发、构建和生产系统的先决条件

在开发、构建和生产系统中，文件权限和所有权必须保持一致。 要使此功能正常工作，您必须执行以下任一操作：

- 以下所有内容：

   - 在所有系统上设置相同的文件系统所有者用户名
   - 确保Web服务器在所有系统上以同一用户的身份运行
   - 确保文件系统所有者位于所有系统的Web服务器组中

- 根据需要使用以下准则更改每个系统的商务文件系统权限和所有权：

   - 开发和构建： [设置预安装所有权和权限（两个用户）](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - 生产： [商业在开发和生产中的所有权和权限](file-system-permissions.md)

>[!INFO]
>
>如果选择此方法，则每次从构建系统中提取代码时，都必须设置文件系统权限和所有权（如果构建系统上的文件系统所有者或Web服务器用户不同）。
