---
title: 使用清漆清除快取
description: 瞭解快取清除如何與Varnish搭配使用，以及如何將其用作Adobe Commerce應用程式的網頁快取加速器。
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 使用清漆清除快取

本主題說明使用Varnish做為Adobe Commerce和Magento Open Source的網頁快取加速器的基本知識。

## 清漆清除

根據 [塗漆檔案](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html)， &quot;A *清除* 是當您從快取中挑選物件並捨棄它及其變體時所發生的情況。」 清漆清除類似於快取清除指令(或按一下 **排清Magento快取** （在「管理員」中）。

事實上，當您清除、排清或重新整理Commerce快取時，清漆也會清除。

安裝並設定Varnish以搭配Commerce使用後，下列動作可能會導致Varnish清除：

- 維護網站。

   例如，您在管理員中執行的任何操作：

   - **商店** > **設定** > **設定** >一般> **一般**
   - **商店** > **設定** > **設定** >一般> **貨幣設定**
   - **商店** > **設定** > **設定** >一般> **存放區電子郵件地址**

   當Commerce偵測到此類變更時，會顯示一則訊息，通知您重新整理快取。

- 維護商店（例如，新增或編輯類別、價格、產品和促銷定價規則）。

   當您執行任何這些工作時，會自動清除清漆。

- 維護原始程式碼。

   您應重新整理快取，並定期刪除 `generated/code` 和 `generated/metadata` 目錄。 如需重新整理快取的詳細資訊，請參閱下一節。

## 設定Commerce清除清漆

使用設定清漆主機後，Commerce會清除清漆主機 [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) 命令。

您可以使用選用引數 `--http-cache-hosts` 引數，用來指定清漆主機和接聽連線埠的逗號分隔清單。 設定所有Varnish主機，無論您有一台或多台。 （請勿以空格字元分隔主機。）

引數格式必須是 `<hostname or ip>:<listen port>`，您可在此省略 `<listen port>` 如果是連線埠80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

當您重新整理Commerce快取時，可以清除Varnish主機(也稱為 *清理* （例如快取）或使用命令列。

若要使用管理員重新整理快取，請按一下 **[!UICONTROL SYSTEM]** >工具> **快取管理**，然後按一下 **排清Magento快取** ，位於頁面頂端。 （您也可以重新整理個別快取型別。）

若要使用命令列重新整理快取，您通常會使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令作為 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
