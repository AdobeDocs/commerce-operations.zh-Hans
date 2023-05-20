---
title: 啟用或停用模組
description: 請依照下列步驟管理Adobe Commerce或Magento Open Source模組。
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 啟用或停用模組

這個命令沒有先決條件。

## 模組狀態

使用下列命令列出已啟用和已停用的模組：

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

位置

* `--enabled` 列出所有已啟用的模組。
* `--disabled` 列出所有已停用的模組。
* `<module-list>` 是以空格分隔的模組清單，用於檢查狀態。 如果任何模組名稱包含特殊字元，請以單引號或雙引號將名稱括住。

## 啟用、停用模組

若要啟用或停用可用的模組，請使用下列命令：

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

位置

* `<module-list>` 是以空格分隔的模組清單，可啟用或停用。 如果任何模組名稱包含特殊字元，請以單引號或雙引號將名稱括住。
* `--all` 以同時啟用或停用所有模組。
* `-f` 或 `--force` 以強制啟用或停用模組，無論是否有相依性。 使用此選項之前，請參閱 [關於啟用和停用模組](#about-enabling-and-disabling-modules).
* `-c` 或 `--clear-static-content` 清除 [產生的靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md).

   如果存在多個同名檔案，但未全部清除，則無法清除靜態檢視檔案可能會導致問題。

   換言之，由於 [靜態檔案遞補](../../configuration/cli/static-view-file-deployment.md) 規則（如果未清除靜態檔案，且有多個名為的檔案） `logo.svg` 不同，後援可能會導致顯示錯誤的檔案。

例如，若要停用 `Magento_Weee` 模組，輸入：

```bash
bin/magento module:disable Magento_Weee
```

如需啟用和停用模組的重要資訊，請參閱 [關於啟用和停用模組](#about-enabling-and-disabling-modules).

## 更新資料庫

如果您啟用一或多個模組，請執行以下命令來更新資料庫：

```bash
bin/magento setup:upgrade
```

然後清除快取：

```bash
bin/magento cache:clean
```

## 關於啟用和停用模組

Adobe Commerce和Magento Open Source可讓您啟用或停用目前可用的模組；換言之，可啟用或停用任何Adobe提供的模組或任何目前可用的協力廠商模組。

某些模組具有對其他模組的相依性，在這種情況下，您可能無法啟用或停用模組，因為它有對其他模組的相依性。

此外，可能會 *衝突* 無法同時啟用的模組。

範例：

* 模組A相依於模組B。除非先停用模組A，否則無法停用模組B。

* 模組A相依於模組B，兩者皆已停用。 您必須先啟用模組B，才能啟用模組A。

* 模組A與模組B衝突。您可以停用模組A和模組B，也可以停用任一模組，但您可以 *無法* 同時啟用模組A和模組B。

* 相依性在 `require` Adobe Commerce和Magento Open Source中的欄位 `composer.json` 每個模組的檔案。 衝突宣告於 `conflict` 模組中的欄位 `composer.json` 檔案。 我們使用該資訊來建立相依性圖表： `A->B` 表示模組A相依於模組B。

* A *相依性鏈結* 是從模組到另一個模組的路徑。 例如，如果模組A相依於模組B，而模組B相依於模組C，則相依性鏈為 `A->B->C`.

如果您嘗試啟用或停用相依於其他模組的模組，相依性圖表會顯示在錯誤訊息中。

>[!NOTE]
>
>模組A有可能是 `composer.json` 會宣告與模組B的衝突，但不會反過來。

*僅限命令列：* 若要強制啟用或停用模組（無論其相依性為何），請使用選填的 `--force` 引數。

>[!NOTE]
>
>使用 `--force` 可能會停用您的存放區，並導致存取管理員時發生問題。
