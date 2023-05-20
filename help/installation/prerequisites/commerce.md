---
title: 取得Adobe Commerce軟體
description: 瞭解如何下載Adobe Commerce和Magento Open Source軟體。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 取得Adobe Commerce軟體

全世界24萬名商戶信任我們的電子商務軟體，而您正是其中之一。 我們已收集一些資訊，以協助您開始安裝。

## 如何取得軟體

檢查是否有令人興奮的新功能和發行版本，並瞭解如何透過我們的 [產品可用性頁面](https://devdocs.magento.com/release/availability.html).

請參閱下表以取得安裝Adobe Commerce或Magento Open Source的快速入門。

<table>
    <tbody>
        <tr>
            <th>使用者需求</th>
            <th>說明</th>
            <th>高階安裝和升級步驟</th>
            <th>開始使用連結</th>
        </tr>
    <tr>
        <td><p>Integrator， packager</p></td>
        <td><p>想要完整控制所有安裝的元件、具有應用程式伺服器的存取權、高度技術性，可能會將Magento Open Source與其他元件重新封裝。</p>
        </td>
        <td><ol><li>建立撰寫器 <em>專案</em> 其中包含要使用的元件清單。</li>
            <li>使用撰寫器更新套件相依性；使用 <code>composer create-project</code> 以取得Composer中繼資料。</li>
            <li>使用安裝應用程式 <a href="../advanced.md">命令列</a>.</li>
        <li>使用升級應用程式和擴充功能  <a href="../../upgrade/implementation/perform-upgrade.md">命令列</a>.</li></ol></td>
        <td><p><a href="../composer.md">取得中繼資料</a></p></td>
    </tr>
    <tr>
        <td><p>參與開發人員</p></td>
        <td><p>會導致Magento Open Source程式碼基底、檔案錯誤和自訂應用程式。 技術含量高，擁有自己的開發伺服器，瞭解Composer和GitHub。</p>
            <p>您 <em>無法</em> 在生產環境中使用應用程式。</p>
      <p>您必須使用升級 <a href="../../upgrade/developer/git-installs.md">Composer和Git命令</a>.</p></td>
        <td><ol><li>複製GitHub存放庫。</li>
            <li>使用撰寫器更新套件相依性。</li>
            <li>安裝應用程式，使用 <a href="../advanced.md">命令列</a>.</li>
            <li>升級應用程式，使用 <a href="../../upgrade/developer/git-installs.md">Composer和Git命令</a>.</li>
            <li>自訂下的程式碼 <code>app/code</code> 目錄。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">複製GitHub存放庫</a></p></td>
    </tr>
    </tbody>
</table>

## 有用的資訊

使用頁面左側的連結，導覽安裝每個部分的主題。

## 必要的伺服器許可權

UNIX系統需要 `root` 安裝及設定軟體（如Web伺服器PHP）的許可權。 如果您需要安裝此軟體，請確定 `root` 存取。

執行 *not* 將應用程式安裝在網頁伺服器docroot中作為 `root` 使用者，因為網頁伺服器可能無法與這些檔案互動。

您需要 `root` 建立下列專案的許可權： [檔案系統擁有者](file-system/overview.md) 並將該擁有者新增至網頁伺服器的群組。 您使用檔案系統擁有者來執行 `bin/magento` 命令列的指令和設定cron工作，為您排程工作。
