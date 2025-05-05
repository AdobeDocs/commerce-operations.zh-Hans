---
title: 大规模分发修补程序的最佳实践
description: 了解Adobe Commerce的集中修补如何帮助您管理企业项目。
role: Developer
feature: Best Practices
badge: label="由Adobe高级技术架构师Tony Evers提供" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="托尼·埃弗斯撰稿"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# 大规模分发Adobe Commerce修补程序的最佳实践

如果您管理多个Adobe Commerce安装，[修补](../../../upgrade/patches/apply.md)可能是一个复杂的过程。 _集中修补_&#x200B;是企业的最佳做法。 它可帮助您在所有Adobe Commerce安装中应用正确的修补程序。 本主题介绍如何为所有类型的Adobe Commerce [修补程序](../../../upgrade/patches/overview.md)实现集中式修补程序分发。

>[!NOTE]
>
>以下内容最初发布在Adobe技术博客上的[按比例分发Adobe Commerce修补程序](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20)帖子中。 它经过了修改，侧重于实施集中修补策略的步骤和代码示例。 请参阅原始文章，以了解有关此处描述的不同修补程序类型的更多详细信息。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 策略

由于存在许多不同类型的修补程序以及应用这些修补程序的多种方法，您如何知道哪个修补程序首先应用？ 您拥有的修补程序越多，它们应用到同一文件或同一行代码的可能性就越大。 修补程序的应用顺序如下：

1. **安全修补程序**&#x200B;是Adobe Commerce版本的静态代码库的一部分。
1. 通过`composer install`和`composer update`插件（如[cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches)），**Composer修补程序**。
1. Commerce[&#128279;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html)程序包的Cloud修补程序中包含所有&#x200B;**必需的修补程序**。
1. 已选择[[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md)中包含的&#x200B;**质量修补程序**。
1. **自定义修补程序**&#x200B;以及`/m2-hotfixes`目录中的Adobe Commerce支持修补程序，按修补程序名称的字母顺序排列。

   >[!IMPORTANT]
   >
   >应用的修补程序越多，代码就越复杂。 复杂的代码会增加升级到新版Adobe商务的难度，并增加您的总拥有成本。

如果您负责维护Adobe Commerce的多个安装，那么确保所有实例都安装了同一组修补程序将是一项困难的挑战。 每个安装都有自己的Git存储库、`/m2-hotfixes`目录和`composer.json`文件。 您拥有的唯一保证是，云用户的&#x200B;**安全修补程序**&#x200B;和&#x200B;**必需的修补程序**&#x200B;都作为主Adobe Commerce版本的一部分安装。

目前，对于此问题，没有单一的集中式解决方案，但Composer提供了一种弥补差距的方法。 [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches)程序包允许您[应用依赖项中的修补程序](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies)。 您可以创建一个可安装所有修补程序的Composer包，然后在您的所有项目中需要该包。

涵盖&#x200B;**安全修补程序**、**必需的修补程序**&#x200B;和&#x200B;**Composer修补程序**，但质量修补程序和`/m2-hotfixes`目录的内容呢？

## 应用高品质的补丁程序和修补程序

您可以使用`vendor/bin/magento-patches apply`命令在云基础架构和内部部署安装上安装质量修补程序。 您必须确保`vendor/bin/magento-patches apply`命令在`composer install`操作之后运行。

>[!NOTE]
>
>在云基础架构上，您还可以通过将质量修补程序列在您的项目的`.magento.env.yaml`文件中来安装质量修补程序。 此处描述的示例要求使用`vendor/bin/magento-patches apply`命令。

您可以指定要应用于自定义编辑器组件包的`composer.json`文件中的修补程序，然后创建在`composer install`操作后运行该命令的插件包。

总之，此集中式打补丁示例要求您创建两个自定义编辑器包：

- **组件包：** `centralized-patcher`

   - 定义要安装的质量修补程序和`m2-hotfixes`的列表
   - 需要`centralized-patcher-composer-plugin`程序包，该程序包在`composer install`操作后运行`vendor/bin/magento-patches apply`命令

- **插件包：** `centralized-patcher-composer-plugin`

   - 定义从`centralized-patcher`包读取质量修补程序列表的`CentralizedPatcher` PHP类
   - 运行`vendor/bin/magento-patches apply`命令以在`composer install`操作后安装质量修补程序列表

### `centralized-patcher`

您可以创建编辑器组件包(`centralized-patcher`)以集中管理所有Adobe Commerce安装中的所有质量修补程序和`/m2-hotfixes`。

组件包必须：

- 在部署期间将`/m2-hotfixes`目录的内容复制到所有安装中。
- 定义要安装的质量补丁程序的列表。
- 运行`vendor/bin/magento-patches`命令以在所有安装中安装相同的质量修补程序列表（使用[`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin)插件包作为依赖项）。

要创建`centralized-patcher`组件包，请执行以下操作：

1. 创建包含以下内容的`composer.json`文件：

   >[!NOTE]
   >
   >以下示例中的`require`属性显示了[插件包](#centralized-patcher-composer-plugin)上的`require`依赖项，在此示例的后面必须创建该依赖项。

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. 在包中创建一个`/m2-hotfixes`目录，并将其添加到`composer.json`文件中的`map`属性。 `map`属性包含要从此包复制到要修补的目标项目根目录中的文件。

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >`centralized-patcher`包将`/m2-hotfixes`目录的内容复制到`composer install`上目标项目的m2-hotfixes目录中。  由于云部署脚本在`composer install`之后应用m2修补程序，因此部署机制将安装所有修补程序。

1. 定义要在`quality-patches`属性中安装的质量修补程序。

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


上述代码示例中的`quality-patches`属性包含[完整修补程序列表](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中的两个修补程序示例。  使用`vendor/bin/magento-patches apply`命令在需要`centralized-patcher`软件包的每个项目中安装这些质量修补程序。

出于测试目的，您可以创建示例修补程序(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`)。

>[!NOTE]
>
>您应该将自己的修补程序与直接从Adobe Commerce支持接收的修补程序一起放在`m2-hotfixes`目录中。

示例修补程序文件(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`)：

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

由于此示例使用本地方法来安装质量修补程序，因此您必须确保`vendor/bin/magento-patches apply`命令在`composer install`操作后运行。 此插件是在运行`vendor/bin/magento-patches apply`命令的`composer install`操作之后触发的。

要创建`centralized-patcher-compose-plugin`组件包，请执行以下操作：

1. 创建包含以下内容的`composer.json`文件：

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. 创建PHP文件并定义`CentralizedPatcher`类以从[`centralized-patcher`](#centralized-patcher)组件包中读取质量修补程序列表，并在每次`composer install`操作后立即安装它们。

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>请参阅[code-examples](#code-examples)，查看此示例中描述的两个包的实际操作情况。


## 如何处理特定于项目的修补程序

您可能会遇到这样的情况：所有项目中仅需要95%的修补程序，而少数修补程序仅适用于特定实例。 应用修补的常规方法仍然有效。 您可以在`/m2-hotfixes`目录中保留特定于项目的修补程序，并为每个项目安装质量修补程序。

如果使用此方法，**不提交`centralized-patcher`组件包复制到您项目的`/m2-hotfixes`目录中的任何修补程序。** 通过将`/m2-hotfixes`添加到您的`.gitignore`文件，您可以防止意外提交。 更新`.gitignore`文件后，请记住，必须使用`git add –force`命令添加任何特定于项目的`/m2-hotfixes`。

## 运行其他Adobe Commerce版本

确保在`centralized-patcher`组件包中设置正确的依赖关系。 例如，您可能需要Adobe Commerce 2.4.5-p2才能获取包的特定版本，该版本仅提供与Adobe Commerce 2.4.5-p2兼容的修补程序。 您可能具有此包的其他版本与Adobe Commerce 2.4.4兼容。

## 了解结果

与云基础架构上的Adobe Commerce一样，本文假定您的部署过程使用`composer install`命令而不是`composer update`或`git pull`将新代码部署到您的服务器。 然后，集中式补丁安装的流程如下所示：

1. Composer安装

   - 安装Adobe Commerce，包括 — p1或 — p2安全和功能修补程序
   - 将集中式`/m2-hotfixes`与项目特定的`/m2-hotfixes`结合起来并支持修补程序并支持修补程序
   - 应用随`cweagans/composer-patches` Composer包一起安装的所有修补程序

1. `composer install`之后

   - Composer插件可安装集中式质量修补程序

1. 部署

   - 基于`.magento.env.yaml`文件安装了所需的补丁程序和特定于项目的质量补丁程序(仅云基础架构项目上的Adobe Commerce)。
   - `/m2-hotfixes`目录中的自定义修补程序和支持修补程序按修补程序名称的字母顺序安装。

这样，您就可以集中管理所有安装的所有修补程序，并且可以更好地保证Adobe Commerce存储的安全性和稳定性。 请使用以下方法检查修补程序状态：

- [云基础架构项目](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [内部部署项目](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## 代码示例

- [Magento Open Source中的集中式修补程序](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Adobe Commerce中云基础架构上的集中式修补程序](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [集中式修补程序编辑器插件](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [集中式修补程序组件](https://github.com/AntonEvers/centralized-patcher)
