---
title: MDVA-41229：可配置产品导入后，前端不显示后端可用的图像
description: MDVA-41229修补程序解决了导入可配置产品后，前端上未显示后端可用图像的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-41229。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Data Import/Export, Configuration, Products
role: Admin
exl-id: 894fdc5b-545c-4ed8-ae1b-573d1d8d3cd6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---

# MDVA-41229：可配置产品导入后，前端不显示后端可用的图像

MDVA-41229修补程序解决了导入可配置产品后，前端上未显示后端可用图像的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-41229。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法）2.3.2-p2和2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可配置产品导入后，前端上可用的图像不会显示在前端上。

<u>重现步骤</u>：

1. 安装干净的Adobe Commerce。
1. 通过转至&#x200B;**商店** > **属性** > **产品** > **添加新属性**&#x200B;来添加自定义属性，其设置如下：

   * 属性：
      * 属性属性：

         * 默认标签：设置大小
         * 商店所有者的目录输入类型：文本样本
         * 所需值：否
         * 更新产品预览图像：是

      * 管理样本（属性的值）：

        | 默认 | 管理员样本 | 管理员描述 | 默认商店视图样本 | 默认商店视图说明 |
        |---|---|---|---|---|
        | 否 | 4 | 4 | 4 | 4 |
        | 否 | 24 | 24 | 24 | 24 |
        | 否 | 30 | 30 | 30 | 30 |
        | 否 | 60 | 60 | 60 | 60 |
        | 否 | 68 | 68 | 68 | 68 |

      * 高级属性属性：

         * 属性代码：set_size
         * 范围：全局
         * 唯一值：否
         * 存储所有者的输入验证：无
         * 添加到列选项：否
         * 在筛选器选项中使用：否

   * 管理标签：

      * 管理标题（大小、颜色等）

         * 默认存储视图：设置大小

   * 店面属性：

      * 在搜索中使用：是
      * 搜索权重：1
      * 在高级搜索中可见：否
      * Storefront上的比较：是
      * 在分层导航中使用：可筛选（包含结果）
      * 在搜索结果分层导航中使用：是
      * 用于促销规则条件：否
      * 在店面的目录页面上可见：是
      * 在产品列表中使用：是
      * 用于产品清单中的排序：否

1. 将此属性添加到产品详细信息组（**商店** > **属性** > **属性集**）内的默认属性集。
1. 将图像集下载到Adobe Commerce根目录内的var文件夹中。
1. 转到&#x200B;**系统** > **数据传输** >并使用以下选项导入文件：

   * 导入设置：

      * 实体类型：产品

   * 导入行为：

      * 导入行为：添加/更新
      * 验证策略：出错时停止
      * 允许的错误数： 1
      * 字段分隔符： `;`
      * 多值分隔符： `,`
      * 属性值常量：EMPTYVALUE
      * 字段存储模块：未选中

   * 要导入的文件：

      * 选择要导入的文件
      * 图像文件目录：将其留空

1. 转到店面到`/product-set.html`页，并在不同的集大小之间切换。 对于“设置大小24”，将没有图库。

<u>预期的结果</u>：

可配置产品中所有简单产品的图库会与所有相关图像一起显示。

<u>实际结果</u>：

产品没有图库。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
