---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# 最佳實務：內容建立工作流程

本檔案說明請求變更或新增的使用者工作流程 *[最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* 中的內容 *Adobe Commerce實施行動手冊*.

## 誰可以建立請求？

Adobe接受來自內部和外部利害關係人的請求，包括但不限於以下群組中的個人：

- Adobe合作夥伴
- AdobeCTAG （客戶技術顧問小組）、客戶支援、客戶成功、工程團隊

## 如何建立請求？

**內部關係人** 可以在COMDOX專案中開啟Jira問題以提交請求。 **外部關係人** 可以透過開啟 [GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 存放庫中。

您可以提交下列型別的請求：

- 新內容的想法
- 已發佈內容的更新
- 發佈利害關係人或社群提供的新內容

## 整體程式為何？


**建立Jira票證或問題** — 內部利害關係人在COMDOX專案中建立Jira票證。 外部利害關係人提交GitHub問題。 在Jira中包含完整詳細資訊或 [GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 協助團隊瞭解內容並排定請求的優先順序。

**Adobe專案團隊會評估請求並排定其優先順序** — 團隊會定期監控要求以確定優先順序，並評估要求的變更，以便納入Implementation Playbook最佳實務。 例如，團隊可能會決定應將請求的內容新增至Experience League或Adobe Developer網站上的現有產品檔案，而不是建立新的最佳實務主題。

如果請求中未提供足夠的資訊，團隊會向請求者要求其他資訊。 如果請求者沒有在14天內回應，團隊會關閉請求。

**建立或更新內容** — 內容建立工作依照「 」中所述的程式完成 [Adobe Experience League投稿人指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). 根據請求，工作可能包括將新內容轉換為Markdown、建立主題或更新現有主題。

**內容檢閱、核准和發佈** — 在建立或更新主題期間，會使用檢閱和編輯內容 [GitHub提取請求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). 所有內容都必須經過編輯稽核。 技術檢閱是選擇性的，視內容而定。 如果不需要技術審查，流程只會繼續編輯審查。 在內容獲得核准之前，此程式可能需要幾個反複專案。

文章獲得核准後，提取請求可以合併至生產分支。 合併應由作者完成。 主題合併後，您可使用手動程式立即發佈至生產環境，或在下次發佈工作執行時自動發佈。 發佈工作通常每兩小時執行一次。

**新內容通知**-Adobe會提供 *新增功能* 區段於 [最佳實務概觀](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) 此主題可讓使用者瞭解最近發佈或更新過的主題。 Adobe也將使用現有管道（例如行銷和內部通訊）來推廣新的最佳實務內容。

## 待處理專案與Kanban面板

為避免重複，已建立並排定優先順序的請求將顯示在COMDOX專案的Jira待辦專案中，並且 [GitHub問題專案](https://github.com/orgs/AdobeDocs/projects/6/views/1). 鼓勵內部利害關係人與Jira的投票系統互動，以投票贊成他們認為必要或相關的請求。 投票也有助於最佳實務專案團隊瞭解利害關係人期望的內容型別和價值。 待定優先順序和稽核的請求會顯示在待處理專案中，直到它們移至Kanban展示板中的作用中通道為止。

內部使用者可以存取Kanban展示板以檢視（和/或監視）正在處理的內容以及進度。 此展示板上只會顯示作用中的請求。
