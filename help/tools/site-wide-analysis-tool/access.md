---
title: 如何存取 [!DNL Site-Wide Analysis Tool]
description: 瞭解如何存取 [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 如何存取 [!DNL Site-Wide Analysis Tool]

此 [!DNL Site-Wide Analysis Tool] 服務位於 [生產模式](https://docs.magento.com/user-guide/magento/installation-modes.html) 的 [!DNL Admin] 具有存取使用者許可權的使用者 [角色資源](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>如果您有內部部署的Adobe Commerce，則必須安裝 [代理程式](../site-wide-analysis-tool/installation.md) ，以使用該工具。

![全網站分析控制面板](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]儀表板*

## 步驟1：驗證許可權

確認 [!DNL Admin] 使用者帳戶擁有存取 [!DNL Site-Wide Analysis Tool] 透過其 [指派的使用者角色](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>此 [!DNL Site-Wide Analysis Tool] 角色資源（許可權）為 **not** 自動指派。 必須為使用者角色啟用，並為中個別指派給每個使用者帳戶的角色啟用 [!UICONTROL Admin].

對於需要的自訂角色 [!DNL Site-Wide Analysis Tool] 存取，請執行下列動作：

1. 選取 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 角色資源。

   ![全網站分析控制面板](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]為角色選取的許可權*

1. 按一下 **[!UICONTROL Save Role]**.

1. 通知任何獲指派該角色的使用者登出 [!DNL Admin]，然後重新登入。

>[!NOTE]
>
>如果您已驗證使用者帳戶具有存取 [!DNL Site-Wide Analysis Tool] 而使用者嘗試從存取工具時收到403錯誤 [!DNL Admin]，您雲端基礎結構上的Adobe Commerce執行個體可能已啟用HTTP存取控制。 此 [!DNL Site-Wide Analysis Tool] 如果您已啟用HTTP驗證，則儀表板不受支援。 如需解決此問題的詳細資訊，請參閱我們的 [支援文章](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

## 步驟2：存取 [!DNL Site-Wide Analysis Tool]

1. 於 *[!UICONTROL Admin]* 側欄，前往 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

1. 閱讀 *使用條款* 的 [!DNL Site-Wide Analysis Tool] 並按一下 **[!UICONTROL Accept]** 以繼續。

   每位使用者都必須接受工作階段的使用條款。 此步驟會針對每個登入工作階段重複執行。

   ![全網站分析控制面板](../../assets/tools/swat-tos.png)
   *使用條款*

1. 在控制面板頂端，按一下您要檢視的標籤。

   ![全網站分析控制面板](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]資訊*

## 步驟3：產生報表

1. 在圖示板的右上角，按一下 **[!UICONTROL Generate Report]**.

1. 選取每個核取方塊 **[!UICONTROL Type]** 和 **[!UICONTROL Priority]** 要納入報表中的設定。

1. 按一下 **[!UICONTROL Generate Report]**.

   ![全網站分析控制面板](../../assets/tools/swat-report-settings.png)
   *報表設定*

| 標籤 | 說明 |
| --- | --- |
| 儀表板 | 依優先順序顯示您系統的健全狀態（包含目前的通知和建議）。 |
| 資訊 | 提供客戶連絡資訊和目前票證的摘要，以及每個已安裝Adobe Commerce產品的詳細資訊。 |
| Recommendations | 根據最佳實務列出建議，以解決在您的網站上偵測到的問題。 |
| 例外 | 列出應用程式因無錯誤處理常式的異常狀況所引發的錯誤。 |
| 擴充功能 | 列出所有協力廠商擴充功能和協力廠商程式庫。 |

>[!NOTE]
>
>套用建議後，可能需要幾天時間才能在 [!DNL Site-Wide Analysis Tool] 儀表板或產生的報告。
