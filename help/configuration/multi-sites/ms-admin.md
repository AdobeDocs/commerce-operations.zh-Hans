---
title: 在“管理员”中设置多个网站、商店和商店视图
description: 在Commerce Admin中配置其他网站、商店和商店视图。
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 0%

---

# 在管理员中设置多个视图

此任务要求您为每个存储创建一个根类别（如果需要，还可以创建其他类别）。 本主题中讨论的任务提供了一种设置多个存储区的方法。 有关其他信息，请参阅《Commerce用户指南》中的以下资源：

- [类别](https://docs.magento.com/user-guide/catalog/categories.html)
- [添加网站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [存储URL](https://docs.magento.com/user-guide/stores/store-urls.html)
- [内容](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>仅出于示例目的，我们使用带有网站代码的法语网站 `french` 在本主题中。 有关分步教程，请参阅 [教程：使用Apache设置多个网站](ms-apache.md) 和 [教程：使用nginx设置多个网站](ms-nginx.md)

## 步骤1：创建根类别

创建根类别是可选的，但我们会在您希望每个网站都有一个唯一的根类别的情况下，在本教程中介绍如何创建根类别。 您可以选择创建其他类别。

要创建根类别，请执行以下操作：

1. 以有权创建类别的用户身份登录到管理员。
1. 单击 **目录** > **类别**.
1. 单击 **添加根类别**.
1. 在 **类别名称** 字段，输入唯一名称以标识此类别。
1. 确保启用类别设置为 **是**.

   有关此页面上其他选项的信息，请参见 [根类别](https://docs.magento.com/user-guide/catalog/category-root.html).

   下图显示了一个示例。

   ![创建和启用根类别](../../assets/configuration/add-root-category.png)

1. 单击 **保存**.
1. 根据需要重复这些任务多次，以便为存储区创建根类别。

## 步骤2：创建网站

要创建网站，请执行以下操作：

1. 以有权创建网站、商店和商店视图的用户身份登录到管理员。
1. 单击 **商店** > **设置** > **所有商店**.
1. 在 _商店_ 页面，单击 **创建网站**.

   - **名称** — 输入用于标识网站的名称。
   - **代码** — 输入唯一代码；例如，如果您有一个法式商店，则可以输入 `french`
   - **排序顺序** — 输入可选的数字排序顺序。

   下图显示了一个示例。

   ![添加网站](../../assets/configuration/multi-site-website.png)

1. 单击 **保存网站**.
1. 创建网站时，根据需要重复这些任务多次。

## 步骤3：创建存储

要创建存储，请执行以下操作：

1. 在 _管理员_ 面板，单击 **商店** > **设置** > **所有商店**.
1. 在 _商店_ 页面，单击 **创建商店**.

   - **网站** — 单击要与此商店关联的网站的名称。
   - **名称** — 输入名称以标识存储。
   - **代码** — 输入唯一代码以标识商店。
   - **根类别** — 单击此存储的根类别的名称。

   下图显示了一个示例。

   ![添加商店](../../assets/configuration/multi-site-store.png)

1. 单击 **保存存储**.
1. 根据需要重复这些任务多次创建存储区。

## 步骤4：创建商店视图

要创建商店视图，请执行以下操作：

1. 在 _管理员_ 面板，单击 **商店** > **设置** > **所有商店**.
1. 在“商店”页面上，单击 **创建商店视图**.

   - **存储** — 单击要与此存储视图关联的存储的名称。
   - **名称** — 输入用于标识此存储视图的名称。
   - **代码** — 输入唯一名称以标识此存储视图。
   - **状态** — 选择 **已启用**.

   下图显示了一个示例。

   ![添加商店](../../assets/configuration/multi-site-storeview.png)

1. 单击 **保存存储视图**.
1. 根据需要重复这些任务多次以创建存储视图。

## 步骤5：更改网站基本URL

使用唯一URL访问网站，例如 `http://french.magento.mg`中，您必须在“管理员”中更改每个站点的基本URL。

要更改网站基本URL，请执行以下操作：

1. 在 _管理员_ 面板，单击 **商店** > **设置** > **配置** > **常规** > **Web**.
1. 从 **商店视图** 列表时，单击其中一个网站的名称，如下图所示。

   ![选择范围](../../assets/configuration/multi-site-scope.png)

1. 在右窗格中，展开 **基本URL**.
1. 在 _基本URL_ 部分，清除 **使用系统值**.
1. 输入 `http://french.magento.mg` 中的URL **基本URL** 和 **基本链接URL** 字段。

1. 在中重复上一步骤 _基本URL（安全）_ 部分。

   >[!INFO]
   >
   >如果要为云基础架构上的Adobe Commerce部署设置基本URL，则必须将第一个时段替换为三个短划线。 例如，如果您的基本URL为 `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`，输入 `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. 如果要设置基本URL以进行本地测试，请使用句点。

1. 单击 **保存配置**.

1. 对其他网站重复这些任务。

## 步骤6：将存储代码添加到基本URL

Commerce为您提供了将商店代码添加到网站基础URL的选项，这简化了设置多个商店的过程。 使用此选项，您无需在Commerce文件系统上创建目录即可存储 `index.php` 和 `.htaccess`.

这样可防止 `index.php` 和 `.htaccess` 在以后的升级中不再与Commerce代码库同步。

请参阅 [Commerce用户指南](https://docs.magento.com/user-guide/stores/store-urls.html).

要将存储代码添加到基本URL，请执行以下操作：

1. 在 _管理员_ 面板，单击 **商店** > **设置** > **配置** > **常规** > **Web**.
1. 从 **商店视图** 列表时，单击 **默认配置** 如下图所示。

   ![选择默认配置范围](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展开 **Url选项**.
1. 清除 **使用系统值** 旁边的复选框 _将存储代码添加到Url_.
1. 从 _将存储代码添加到Url_ 列表，单击 **是**.

   ![将商店代码添加到商店基本URL](../../assets/configuration/multi-site-add-store-url.png)

1. 单击 **保存配置**.
1. 如果出现提示，请刷新缓存。 (**系统** > **缓存管理**)。

## 步骤7：更改默认存储视图基本URL

您必须在最后执行此步骤，因为您将失去对管理员的访问权限；在您设置虚拟主机后，您的访问权限将返回，如特定于Web服务器的主题中所述。

要更改默认存储视图基本URL，请执行以下操作：

1. 在 _管理员_ 面板，单击 **商店** > **设置** > **配置** > **常规** > **Web**.

1. 从 _商店视图_ 列表时，单击 **默认配置**.

   ![选择默认配置范围](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展开 **基本URL**.
1. 在 _基本URL_ 部分，清除 **使用系统值**.
1. 输入 `http://magento.mg` 中的URL **基本URL** 和 **基本链接URL** 字段。

1. 在中重复上一步骤 **基本URL（安全）** 部分。

   >[!INFO]
   >
   >如果您在云基础架构上为Adobe Commerce设置基本URL，则必须将第一个句点替换为三个短划线。 例如，如果您的基本URL为 `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`，输入 `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. 单击 **保存配置**.
