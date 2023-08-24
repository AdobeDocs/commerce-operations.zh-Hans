---
title: 大规模分发修补程序的最佳实践
description: 了解Adobe Commerce的集中修补如何帮助您管理企业项目。
role: Developer
feature: Best Practices
badge: label="由Adobe高级技术架构师Anton Evers提供" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="安东·埃弗斯撰写"
source-git-commit: d8ee656b4b1741b39f2eef1f5628a299377e774c
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# 大规模分发Adobe Commerce修补程序的最佳实践

如果您管理多个Adobe Commerce安装， [修补](../../../upgrade/patches/apply.md) 可能会是一个复杂的过程。 _集中修补_ 是的重要组成部分 [全球参考体系结构](../../architecture/global-reference.md) 也是企业的最佳实践。 它可帮助您在所有Adobe Commerce安装中应用正确的修补程序。 本主题介绍如何为所有类型的Adobe Commerce实现集中式修补程序分发 [补丁程序](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>以下内容最初发布在 [大规模分发Adobe Commerce修补程序](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) 在Adobe技术博客上发帖。 它经过了修改，侧重于实施集中修补策略的步骤和代码示例。 请参阅原始文章，以了解有关此处描述的不同修补程序类型的更多详细信息。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 策略

由于存在许多不同类型的修补程序以及应用这些修补程序的多种方法，您如何知道哪个修补程序首先应用？ 您拥有的修补程序越多，它们应用到同一文件或同一行代码的可能性就越大。 修补程序的应用顺序如下：

1. **安全修补程序** 是Adobe Commerce版本的静态代码库的一部分。
1. **Composer修补程序** 到 `composer install` 和 `composer update` 插件，例如 [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. 全部 **所需的修补程序** 包含在 [Commerce云修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) 包。
1. 已选择 **高质量的补丁程序** 包含在 [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **自定义修补程序** 和Adobe Commerce支持中的修补程序 `/m2-hotfixes` 目录按修补程序名称的字母顺序。

   >[!IMPORTANT]
   >
   >应用的修补程序越多，代码就越复杂。 复杂的代码会增加升级到新版Adobe商务的难度，并增加您的总拥有成本。

如果您负责维护Adobe Commerce的多个安装，那么确保所有实例都安装了同一组修补程序将是一项困难的挑战。 每个安装都有自己的Git存储库， `/m2-hotfixes` 目录，和 `composer.json` 文件。 您唯一能保证的是 **安全修补程序** 和 **所需的修补程序** for cloud用户都作为主Adobe Commerce版本的一部分进行安装。

目前，对于此问题，没有单一的集中式解决方案，但Composer提供了一种弥补差距的方法。 此 [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) 包允许您 [应用依赖项中的修补程序](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). 您可以创建一个可安装所有修补程序的Composer包，然后在您的所有项目中需要该包。

涵盖 **安全修补程序**， **所需的修补程序**、和 **Composer修补程序**，但质量补丁和内容如何 `/m2-hotfixes` 目录？

## 应用高品质的补丁程序和修补程序

您可以使用以下工具在云基础架构和内部安装上安装质量补丁程序 `vendor/bin/magento-patches apply` 命令。 您必须确保 `vendor/bin/magento-patches apply` 命令运行于 `composer install` 操作。

>[!NOTE]
>
>在云基础架构上，您还可以通过在项目的 `.magento.env.yaml` 文件。 此处描述的示例要求使用 `vendor/bin/magento-patches apply` 命令。

您可以指定要应用的修补程序 `composer.json` 自定义编辑器组件包的文件，然后创建一个插件包，该插件包随后运行命令 `composer install` 操作。

总之，此集中式打补丁示例要求您创建两个自定义编辑器包：

- **组件包：** `centralized-patcher`

   - 定义质量修补程序的列表和 `m2-hotfixes` 安装
   - 需要 `centralized-patcher-composer-plugin` 包，用于运行 `vendor/bin/magento-patches apply` 命令晚于 `composer install` 操作

- **插件包：** `centralized-patcher-composer-plugin`

   - 定义 `CentralizedPatcher` 从读取质量修补程序列表的PHP类 `centralized-patcher` 包
   - 运行 `vendor/bin/magento-patches apply` 命令以安装质量修补程序列表 `composer install` 操作

### `centralized-patcher`

您可以创建Composer组件包(`centralized-patcher`)，以集中管理所有高质量的修补程序和 `/m2-hotfixes` 在所有Adobe Commerce安装中进行归因、分段、流程、流失等操作。

组件包必须：

- 复制 `/m2-hotfixes` 在部署期间将目录发送到所有安装中。
- 定义要安装的质量补丁程序的列表。
- 运行 `vendor/bin/magento-patches` 命令在所有安装中安装相同的质量修补程序列表(使用 [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) 插件包)。

要创建 `centralized-patcher` 组件包：

1. 创建 `composer.json` 文件包含以下内容：

   >[!NOTE]
   >
   >此 `require` 以下示例中的属性显示 `require` 依赖于 [插件包](#centralized-patcher-composer-plugin) 稍后必须创建此示例。

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

1. 创建 `/m2-hotfixes` directory并将其添加到 `map` 属性位于 `composer.json` 文件。 此 `map` 属性包含要从此包复制到要修补的目标项目的根目录中的文件。

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
   >此 `centralized-patcher` 包将复制 `/m2-hotfixes` 目录添加到上的目标项目的m2-hotfixes目录中 `composer install`.  由于云部署脚本在以下位置应用m2修补程序： `composer install`，则所有修补程序都将通过部署机制安装。

1. 定义要在中安装的质量修补程序 `quality-patches` 属性。

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


此 `quality-patches` 前面的代码示例中的属性包含两个修补程序，它们来自 [完整修补程序列表](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 举个例子。  每个需要 `centralized-patcher` 使用打包 `vendor/bin/magento-patches apply` 命令。

出于测试目的，您可以创建一个示例修补程序(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`)。

>[!NOTE]
>
>您应该将自己的修补程序放在 `m2-hotfixes` 目录，以及您直接从Adobe Commerce支持部门收到的修补程序。

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

由于此示例使用本地方法来安装质量修补程序，因此您必须确保 `vendor/bin/magento-patches apply` 命令运行于 `composer install` 操作。 此插件在以下时段后触发： `composer install` 操作，运行 `vendor/bin/magento-patches apply` 命令。

要创建 `centralized-patcher-compose-plugin` 组件包：

1. 创建 `composer.json` 文件包含以下内容：

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

1. 创建PHP文件并定义 `CentralizedPatcher` 类以从读取质量修补程序列表 [`centralized-patcher`](#centralized-patcher) 组件包，并在每隔 `composer install` 操作。

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
>请参阅 [代码示例](#code-examples) 查看本示例中所述的两个包的实际操作情况。


## 如何处理特定于项目的修补程序

您可能会遇到这样的情况：所有项目中仅需要95%的修补程序，而少数修补程序仅适用于特定实例。 应用修补的常规方法仍然有效。 您可以在中保留特定于项目的修补程序 `/m2-hotfixes` 目录和安装每个项目的质量修补程序。

如果你用这种方法， **不要** 提交中的任何修补程序 `/m2-hotfixes` 已由复制到您项目中的目录 `centralized-patcher` 组件包。 您可以通过添加以下内容防止意外提交 `/m2-hotfixes` 敬您的 `.gitignore` 文件。 更新后 `.gitignore` 文件，请记住， `/m2-hotfixes` 必须使用添加 `git add –force` 命令。

## 运行其他Adobe Commerce版本

确保您在中设置了正确的依赖关系 `centralized-patcher` 组件包。 例如，您可能需要Adobe Commerce 2.4.5-p2才能获取包的特定版本，该版本仅提供与Adobe Commerce 2.4.5-p2兼容的修补程序。 您可能具有此包的其他版本与Adobe Commerce 2.4.4兼容。

## 了解结果

与云基础架构上的Adobe Commerce一样，本文假定您的部署过程使用 `composer install` 命令而非 `composer update` 或 `git pull` 以将新代码部署到您的服务器。 然后，集中式补丁安装的流程如下所示：

1. Composer安装

   - 安装Adobe Commerce，包括 — p1或 — p2安全和功能修补程序
   - 集集中式于一体 `/m2-hotfixes` 并支持带有项目特定修补程序的修补程序 `/m2-hotfixes` 和支持修补程序
   - 应用随安装的任何修补程序 `cweagans/composer-patches` Composer包

1. 之后 `composer install`

   - Composer插件可安装集中式质量修补程序

1. 部署

   - 所需的补丁程序和特定于项目的质量补丁程序的安装基于 `.magento.env.yaml` 文件(仅限Adobe Commerce云基础架构项目)。
   - 自定义修补程序以及支持来自的修补程序 `/m2-hotfixes` 目录按修补程序名称的字母顺序进行安装。

这样，您就可以集中管理所有安装的所有修补程序，并且可以更好地保证Adobe Commerce存储的安全性和稳定性。 请使用以下方法检查修补程序状态：

- [云基础架构项目](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [内部部署项目](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## 代码示例

- [Magento Open Source中的集中式修补程序](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Adobe Commerce中针对云基础架构的集中式修补程序](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [集中式补丁程序编辑器插件](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [集中式补丁程序组件](https://github.com/AntonEvers/centralized-patcher)
