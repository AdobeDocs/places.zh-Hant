---
title: 測試和驗證Places服務
description: 本節提供如何測試和驗證Places Service的相關資訊。
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 2%

---

# Recommendations將測試Places服務 {#test-validate-loc-svc}

許多客戶和組織將定義全球範圍內的POI，因此，有一種方法來模擬和測試Places Service與您的應用程式的交互方式非常重要。 此資訊可協助您了解如何根據定義的POI和使用者的目前位置，測試及驗證正確觸發的Places Service登入與退出。

由於環境變數可能是位置訊號和準確度的因素，因此我們建議您先透過使用開發人員工具和模擬位置項目進行本機作業，以建立基線結果。 目標是驗證所有位置事件皆正確運作。 在正確驗證位置事件後，即可測試解決方案整合（例如Analytics、Target和Campaign）。 為協助您的測試活動，您應使用回傳設定SlackWebhook，並在個別開發環境中載入GPX檔案。

>[!IMPORTANT]
>
>此計畫假設已在 [Places服務UI](https://places.adobe.com) 而且已安裝並正確設定最新版的Places擴充功能。 如果執行活動區域監視，則還假設實施區域監視解決方案。 如需詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md), [CoreLocation檔案](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) 針對iOS，或 [Android位置檔案](https://developer.android.com/training/location/geofencing).

| 步驟 ： | 說明 | 預期結果 |
|--- |--- |--- |
| 1 | 確認已為Android輸入正確的資訊清單索引鍵，以授與追蹤位置的存取權。 | 已確認 |
| 1a | 確認已在iOS中設定位置更新。 同時，請確定您在iOS中設定了適當的清單金鑰，以要求使用者有權追蹤位置。 | 已確認 |
| 2 | 確認已為iOS設定哪個監控模式。 連續模式允許更高的精確度和持久性，但也能更大地消耗電池壽命。 | 重大變動或持續 |
| 3 | 如果使用多個POI資料庫，請確認已在Places擴充功能中選取適當的資料庫以進行Experience Platform Launch。 | 已確認 |
| 4 | 確認最新版的Mobile Core and Places擴充功能已透過Gradle或CocoaPods與應用程式搭配。 | 已確認 — 如需最近更新的詳細資訊，請參閱 [發行說明。](/help/release-notes.md) |
| 5 | 確認已為測試設定正確的環境。 Launch環境ID應與您的Launch開發環境相符。 | 已確認 |
| 6 | 為每個您要測試的POI建立GPX檔案。 GPX檔案可用於本機開發環境，以模擬位置項目。 有關建立和使用GPX檔案的資訊，請參閱以下內容： <br>[iOS模擬器的GPX檔案[已關閉]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[行動應用程式中的位置測試](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX檔案會在應用程式專案中建立並載入。 |
| 7 | 若不執行其他動作，您應該可以從Android Studio或XCode啟動應用程式，並查看適當的警報，以要求追蹤位置的存取權。 按一下 *一律允許* 權限。<br><br>建議您使用連接到電腦的實際裝置，而非使用裝置模擬器。 | 應在通過IDE載入的應用程式上顯示位置請求提示 |
| 8 | 接受「位置」權限後。 Places SDK將可擷取裝置的目前位置，而地區監控程式碼應會開始監控來自目前位置的20個最接近的POI | 請參閱表格下的記錄範例。 |
| 9 | 在XCode或Android Studio中的不同位置之間切換時，應會針對特定POI產生登入事件。 進入POI時應會顯示下列記錄。 | 請參閱表格下的記錄範例。 |
| 10 | 區域監視器找到附近的POI後，您應將位置Ping傳送出去以進行測試。 在Launch中，建立新規則，此規則會根據地域圍欄項目使用Places擴充功能觸發。 然後使用行動核心建立新動作以傳送回傳。 建立SlackWebhook應用程式可協助您查看位置登入點和退出點。 如需建立SlackWebhook應用程式的詳細資訊，請參閱 [使用傳入的Webhook傳送訊息。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 在Launch中，請確定您已為Places擴充功能新增資料元素，其中包括： <br>目前的POI名稱<br>目前POI緯度<br>當前POI長<br>上次輸入的名稱<br>上次輸入的最後<br>上次輸入長<br>上次退出名稱<br>上次退出時間<br>上次退出長<br>時間戳記 |  |
| 10b | 使用Event = Places → Enter POI建立新規則 |  |
| 10c | 建立動作=行動核心→回傳 |  |
| 10d | 使用您的Slack應用程式的網頁連結URL，例如https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | 貼文內容類似： `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>請確定您使用此處建立的特定資料元素。 |  |
| 10f | 請確定您在Launch中發佈所有新資料元素和規則變更。 （您應在Launch介面的右上方選取正常的開發程式庫。） |  |
| 11 | 在開發人員IDE中的GPX位置之間翻轉，以啟動並再次測試您的應用程式。 | 現在，當您在開發環境中選取不同位置時，應該會看到Slack通知顯示每個POI的項目。 |
|  | **快速摘要點**<br>&#x200B;所有這些測試都可在本機進行，而無須前往特定POI位置。 驗證測試有助於確保您的應用程式已正確設定，且已收到該位置的正確權限。 <br><br>此驗證也可讓您確信，定義的POI可搭配您的地區監控實作正常運作。  在此步驟之後，我們將開始測試Campaign中的訊息，以根據POI登入和退出來查看是否顯示正確的訊息。 |  |
|  | **使用Places服務測試Adobe Campaign Standard應用程式內傳訊。** |  |
| 12 | 在主要的Campaign控制面板上，設定新的應用程式內訊息（類型=廣播） |  |
| 12a | 在觸發器中，選取 **放置事件類型 — 以登入作為觸發器**. |  |
| 12b | 選擇 **[!UICONTROL 放置自訂中繼資料]** 作為其他篩選 — 使用POI類型=上次輸入的POI。<br>我們使用 **[!UICONTROL 上次輸入]** 作為POI類型，因為在大多數情況下， **[!UICONTROL 上次輸入]** 將與相同 **[!UICONTROL 目前POI]**. <br><br>**[!UICONTROL 目前POI ]**只應在有重疊的POI地理圍欄時使用。 在此情況下，這些POI必須是「排名」，然後是**[!UICONTROL &#x200B;目前POI ]**會顯示使用者目前可能所在的2或3個地域範圍中排名最前的POI。 |  |
| 12c | 選取自訂中繼資料索引鍵，協助您縮小將接收訊息的POI範圍。 |  |
| 12d | 對於頻率和持續時間，請僅保留一或兩天，這樣一來，如果您不喜歡條件，可以在較短的時間內讓觸發器過期。 |  |
| 12e | 對於「一律/一次」或「直到點進」，請選取 *一律* 以便您可以跨多個位置進行測試。 | 當您模擬符合適當中繼資料條件的位置變更時，「一律」會顯示應用程式內訊息。 |
| 12f | 為顯示，選取「本機通知」以外的選項。 這可讓您在前景使用應用程式進行測試時更容易查看。) |  |
| 12g | 準備/確認並部署應用程式內訊息。 |  |
| 13 | 在您的開發環境中，為了確保下載新的促銷活動規則，請結束並再次啟動應用程式。 | 別忘了必須再次完全啟動應用程式，新的Campaign規則檔案才能下載至裝置。 |
| 14 | 在您的開發應用程式中，使用先前建立的GPX檔案來切換位置。 | 您應該會根據先前設定的條件，看到應用程式內訊息出現。 |
| 15 | 在下次測試中，我們基本上會複製與之前相同的步驟，但這次我們會測試本機通知。 | 預期的結果是，每次符合符合標準時，都會顯示本機通知。 |
| 16 | 設定新的應用程式內訊息（類型=廣播）。 |  |
| 16a | 在觸發器中，選取 **[!UICONTROL Places事件類型]** - **[!UICONTROL 以登入作為觸發器]**. |  |
| 16b | 選取「放置自訂中繼資料」作為其他篩選 — 使用 **[!UICONTROL POI類型]** = **[!UICONTROL 上次輸入的POI]**. |  |
| 16c | 選取自訂中繼資料索引鍵，協助您縮小將接收訊息的POI範圍。 |  |
| 16d | 對於頻率和持續時間，請僅保留一或兩天，這樣一來，如果您不喜歡條件，可以在較短的時間內讓觸發程式過期。 |  |
| 16e | 對於「一律/一次」或「直到點進」， **[!UICONTROL 一律]**. |  |
| 16f | 對於顯示類型，請選擇 **[!UICONTROL 本機通知]**. |  |
| 16g | 準備/確認並部署應用程式內訊息。 |  |
| 17 | 在開發人員環境中，連接您的裝置並按 **[!UICONTROL 播放]** 在組建中。 建立該位置後，請對應用程式設定背景，並繼續在Xcode或Android Studio中切換位置。 您仍應會看到指出位置變更的主控台讀取畫面，而且您也應該會看到顯示的本機通知，視觸發器中設定的條件而定。 （可能會延遲1至2秒。） | 預期的結果是，每次符合相符標準時，都會顯示本機通知。 |
|  | **摘要點** <br>目前，我們應該會在本機環境中看到POI項目。 我們也應該會根據POI工作，看到Campaign傳送的訊息。 如果失敗，請檢查以查看Slack通知是否未結束。 如果沒有Slack消息，請檢查應用程式控制台，因為可能尚未記錄新的位置項。 如果結果成功，我們就可以相當確定應用程式是否正常運作，以及Places Service和Campaign傳訊服務是否也正常運作。 |  |
|  | **現場測試** <br>在位置上進行測試時，應該不會有太大改變。 讓閒置的回傳保持作用中，應有助於了解裝置是否收到該位置的登入和退出訊息。 |  |
| 18 | 在以禁用wifi和行動電話開始的設備上進行測試，然後在POI區域中啟用一次。 | 如果發生失敗，請記下您是否在Slack中收到地域圍欄項目和通知。 Slack通知的時間戳記為何？ |
| 19 | 在僅啟用蜂窩且關閉wifi的情況下進行測試。 |  |
| 20 | 開啟行動電話和wifi後進行測試。 |  |
|  | **摘要點** <br>現場測試應與開發測試緊密相符。 請記得，在決定使用者位置時可能會發生一些環境因素，例如POI地域圍欄所花的時間長度、信號可用性，以及附近wifi存取點的強度。 |  |

## 日誌示例

**步驟8 :** 位置更新期間需要的iOS和Android記錄

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**步驟9 :** 事件期間需要的iOS和Android記錄

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
