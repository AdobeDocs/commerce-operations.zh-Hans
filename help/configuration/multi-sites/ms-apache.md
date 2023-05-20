---
title: 使用Apache設定多個網站
description: 按照本教學課程中的說明使用Apache設定多個網站。
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# 使用Apache設定多個網站

我們假設：

如有必要，請複製現有的 `index.php` 網站或商店檢視的進入點指令碼，並將其新增至下列專案：

- 您正在使用開發機器（筆記型電腦、虛擬機器器等）

   在託管環境中部署多個網站可能需要執行其他工作；如需詳細資訊，請洽詢您的託管提供者。

   在雲端基礎結構上設定Adobe Commerce需要其他工作。 完成本主題中討論的任務後，請參閱 [設定多個網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _雲端基礎結構上的Commerce指南_.

- 每個網站使用一個虛擬主機；虛擬主機設定檔案為 `/etc/httpd/httpd.conf`

   不同作業系統上的不同Apache版本會以不同方式設定虛擬主機。 請參閱 [Apache檔案](https://httpd.apache.org/docs/2.4/vhosts) 或網路管理員（如果您不確定如何設定虛擬主機）。

- Commerce軟體安裝在 `/var/www/html/magento2`
- 您有預設以外的兩個網站：

   - `french.mysite.mg` 使用網站程式碼 `french` 和存放區檢視代碼 `fr`
   - `german.mysite.mg` 使用網站程式碼 `german` 和存放區檢視代碼 `de`

## 使用Apache設定多個網站的藍圖

設定多個存放區包含下列工作：

1. [設定網站、商店和商店檢視](ms-admin.md) 在Admin中。
1. 建立一個 [Apache虛擬主機](#step-2-create-apache-virtual-hosts) 每個Commerce網站。

## 步驟1：在「管理員」中建立網站、商店和商店檢視

另請參閱 [在「管理員」中設定多個網站、商店和商店檢視](ms-admin.md).

## 步驟2：建立Apache虛擬主機

本節討論如何設定下列專案的值： `MAGE_RUN_TYPE` 和 `MAGE_RUN_CODE` 使用Apache伺服器變數 `SetEnvIf` 在虛擬主機中。

如需有關的詳細資訊 `SetEnvIf`，請參閱：

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**建立Apache虛擬主機的方式**：

1. 作為使用者，具有 `root` 許可權，在文字編輯器中開啟虛擬主機組態檔。

   例如，開啟 `/etc/httpd/conf/httpd.conf`

1. 找到開頭為的區段 `<VirtualHost *:80>`.
1. 在任何現有虛擬主機之後建立下列虛擬主機：

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. 將變更儲存至 `httpd.conf` 並退出文字編輯器。
1. 重新啟動Apache：

   - CentOS： `service httpd restart`
   - Ubuntu： `service apache2 restart`

## 驗證您的網站

除非您為商店的URL設定了DNS，否則您必須將靜態路由新增到中的主機。 `hosts` 檔案：

1. 找到您的作業系統 `hosts` 檔案。
1. 以下列格式新增靜態路由：

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 前往瀏覽器中的下列URL之一：

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在託管環境中部署多個網站可能需要執行其他工作；如需詳細資訊，請洽詢您的託管提供者。
>- 在雲端基礎結構上設定Adobe Commerce需要其他工作；請參閱 [設定多個Cloud網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _雲端基礎結構上的Commerce指南_.


### 疑難排除

- 如果您的法文和德文網站傳回404s，但您的管理員載入，請確定您已完成 [步驟6：將商店程式碼新增至基底URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 如果所有URL都傳回404s，請確定您已重新啟動網頁伺服器。
- 如果管理員無法正常運作，請確定您正確設定虛擬主機。
