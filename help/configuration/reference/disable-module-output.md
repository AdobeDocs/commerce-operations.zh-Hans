---
title: 禁用模块输出
description: 了解如何禁用模块输出。
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: fee09845777e23717e618ac57df4158d6b172d4f
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# 禁用模块输出

默认情况下，所有模块都进行了配置，以便可以将模块输出写入视图。 关闭输出提供了一种方法，可让您基本上禁用由于硬依赖关系而无法禁用的模块。

例如，`Customer`模块依赖于`Review`模块，因此无法禁用`Review`模块。 但是，如果您不希望客户提供审核，则可以关闭`Review`模块的输出。

>[!INFO]
>
>如果商家在以前的版本中使用管理员禁用模块输出，则必须手动配置系统以迁移这些设置。

禁用输出操作在以下类中执行：

- [\Magento\Framework\View\Element\AbstractBlock：：toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template：：isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>禁用模块输出不会禁用模块。 模块保持已启用状态并正常工作，但前端或后端上未呈现块、页面或字段。

## 在管道部署中禁用模块输出

要在具有Commerce应用程序的多个实例的管道部署或任何其他部署中禁用模块输出，请执行以下操作：

1. 编辑`Backend`模块的`config.xml`文件。
1. 导出配置更改。

### 编辑`Backend`模块`config.xml`文件

1. 存档原始`config.xml`文件。
1. 在`<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml`文件中直接在`<default>`元素下添加与以下内容类似的行：

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   此处：

   - `<modules_disable_output>`包含模块列表。
   - `<Magento_Newsletter></Magento_Newsletter>`指定要禁用输出的模块。
   - `1`是禁用`Magento_Newsletter`模块输出的标志。

作为此配置的示例结果，客户无法再注册接收新闻稿。

### 导出配置更改

运行以下命令以导出配置更改：

```bash
bin/magento app:config:dump
```

结果将写入`<Magento_install_dir>/app/etc/config.php`文件。

接下来，清除缓存以启用新设置：

```bash
bin/magento cache:clean config
```

请参阅[导出配置](../cli/export-configuration.md)。

## 在简单部署中禁用模块输出

在Commerce的单个实例上禁用模块输出的过程更简单，因为不必分发更改。

1. 存档原始`<Magento_install_dir>/app/etc/config.php`文件。
1. 将`advanced`和`modules_disable_output`部分添加到`config.php`文件（如果它们不存在）：

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

在此示例中，`Magento_Review`模块的输出已被禁用，客户无法再查看产品。

### 重新启用模块输出

要重新启用输出，请将模块的值设置为`0`，或者从`config.php`文件中删除行/模块。
