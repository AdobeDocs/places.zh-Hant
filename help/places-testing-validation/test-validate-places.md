---
title: 測試及驗證Places服務
description: 本節提供如何測試及驗證Places服務的相關資訊。
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 2%

---

# Recommendations可測試Places Service {#test-validate-loc-svc}

全球有許多客戶和組織會定義POI，因此請務必模擬及測試Places服務與應用程式的互動方式。 此資訊可協助您瞭解如何測試及驗證Places服務專案及退出，這些專案會根據定義的POI和使用者的目前位置正確觸發。

由於環境變數可能是位置訊號與準確度的一個因素，因此我們建議您先使用開發人員工具和模擬位置專案在本機工作，以建立基準結果。 目標是驗證所有位置事件是否正常運作。 在正確驗證位置事件後，即可測試解決方案整合（例如Analytics、Target和Campaign）。 為了協助您的測試活動，您應該使用回傳來設定SlackWebhook，並在個別開發環境中載入GPX檔案。

>[!IMPORTANT]
>
>此計畫假設POI已建立於 [Places Service UI](https://places.adobe.com) 以及已安裝並正確設定最新版Places擴充功能。 執行主動式區域監控時，也會假設已實作區域監控解決方案。 如需詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)， [CoreLocation檔案](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) 適用於iOS，或 [Android位置檔案](https://developer.android.com/training/location/geofencing).

| 步驟 | 說明 | 預期結果 |
|--- |--- |--- |
| 1 | 確認已輸入Android適用的資訊清單金鑰，以授予追蹤位置的存取權。 | 已確認 |
| 1a | 確認已在iOS中設定位置更新。 同時請確定您已在iOS中設定適當的資料夾索引鍵，以請求使用者追蹤位置的許可權。 | 已確認 |
| 2 | 確認為iOS設定的監視模式。 連續模式可提供更高的精確度和持續性，但也會大幅減少電池續航力。 | 重大變更或持續 |
| 3 | 如果使用多個POI程式庫，請確認已在Places擴充功能中選取適當的程式庫進行Experience Platform Launch。 | 已確認 |
| 4 | 確認應用程式已透過Gradle或CocoaPods隨附最新版的Mobile Core和Places擴充功能。 | 已確認 — 如需最近更新的詳細資訊，請參閱 [發行說明。](/help/release-notes.md) |
| 5 | 確認測試設定了正確的環境。 Launch環境ID應與您的Launch開發環境相符。 | 已確認 |
| 6 | 為您要測試的每個POI建立GPX檔案。 GPX檔案可用於本機開發環境中，以模擬位置專案。 如需有關建立和使用GPX檔案的資訊，請參閱下列內容： <br>[iOS模擬器的GPX檔案[已關閉]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[行動應用程式中的位置測試](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX檔案會在應用程式專案中建立及載入。 |
| 7 | 您無需執行任何其他操作，即可從Android Studio或Xcode啟動應用程式，並檢視適當的警報以請求追蹤位置的存取權。 按一下 *永遠允許* 許可權。<br><br>建議您使用連線至電腦的真實裝置，而非使用裝置模擬器。 | 位置要求提示應顯示在透過IDE載入的應用程式上 |
| 8 | 接受位置許可權後。 Places SDK將擷取裝置的目前位置，而區域監控程式碼應開始從目前位置監控20個最近的POI | 請參閱表格下方的記錄範例。 |
| 9 | 在Xcode或Android Studio中的不同位置之間切換時，應該會產生特定POI的登入事件。 進入POI時應有以下記錄。 | 請參閱表格下方的記錄範例。 |
| 10 | 在區域監視器找到附近的POI後，您應該透過傳送位置Ping來進行測試。 在Launch中，建立使用Places擴充功能的新規則，以根據地理圍欄專案觸發。 然後使用行動核心建立新動作以傳送回傳。 建立SlackWebhook應用程式可協助您檢視位置專案與退出點。 如需建立SlackWebhook應用程式的詳細資訊，請參閱 [使用傳入的Webhook傳送訊息。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 在Launch中，請確定您已為Places擴充功能新增資料元素，包括： <br>目前的POI名稱<br>目前的POI緯度<br>目前的POI長度<br>上次輸入的名稱<br>上次輸入時間<br>上次輸入時間過長<br>上次退出名稱<br>上次退出時間<br>上次退出時間過長<br>時間戳記 |  |
| 10b | 以「事件=地點→輸入POI」建立新規則 |  |
| 10c | 建立動作=行動核心→回傳 |  |
| 10d | 使用您Slack應用程式的Webhook URL，例如https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD...。 |  |
| 10e | 貼文內文將類似於： `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>請確定您使用您在這裡建立的特定資料元素。 |  |
| 10f | 請務必在Launch中發佈所有新的資料元素和規則變更。 （您應在Launch介面的右上角選取有效的開發程式庫。） |  |
| 11 | 在開發人員IDE中的GPX位置之間切換，再次啟動並測試您的應用程式。 | 現在，當您在開發環境中選取不同位置時，應該會看到Slack通知，顯示每個POI的專案。 |
|  | **快速摘要點**<br>&#x200B;所有測試都可以在本機執行，不必前往特定的POI位置。 驗證測試可協助確保您的應用程式已正確設定，並且已收到位置的正確許可權。 <br><br>此驗證也可讓您確信定義的POI可搭配您的區域監控實作正常運作。  在此步驟後，我們將開始在Campaign中測試傳訊，以檢視是否根據POI專案及退出而顯示正確的訊息。 |  |
|  | **使用Places服務測試Adobe Campaign Standard應用程式內傳訊。** |  |
| 12 | 在Campaign主要控制面板上，設定新的應用程式內訊息（型別=廣播） |  |
| 12a | 在觸發器中，選取 **Places事件型別 — 作為觸發器的專案**. |  |
| 12b | 選取 **[!UICONTROL Places自訂中繼資料]** 作為額外篩選器 — 使用POI型別=上次輸入的POI。<br>我們使用 **[!UICONTROL 上次輸入]** 作為POI型別，因為大多數情況下， **[!UICONTROL 上次輸入]** 將與 **[!UICONTROL 目前的POI]**. <br><br>**[!UICONTROL 目前的POI ]**應僅在存在重疊POI地理柵欄的情況下使用。 在此情況下，這些POI需要排名，然後**[!UICONTROL &#x200B;目前的POI ]**將顯示使用者目前可能所在的2或3個地理柵欄中的排名最前的POI。 |  |
| 12c | 選取自訂中繼資料索引鍵，協助您縮小將接收訊息的POI範圍。 |  |
| 12d | 對於頻率和持續時間，僅保留一或兩天，這樣如果您不喜歡該條件，可以在較短的時間內讓觸發程式過期。 |  |
| 12e | 對於「一律/一次」或「直到點進」，請選取 *一律* 以便您跨多個位置進行測試。 | 當您模擬符合適當中繼資料條件的位置變更時，應用程式內訊息會一律顯示。 |
| 12f | 對於顯示，請選取「本機通知」以外的選項。 這可讓您在前景中使用應用程式進行測試時更容易檢視。) |  |
| 12g | 準備/確認並部署應用程式內訊息。 |  |
| 13 | 在您的開發環境中，為確保下載新的行銷活動規則，請結束並再次啟動應用程式。 | 別忘了，應用程式必須再次完全啟動，新Campaign規則檔案才會下載至裝置。 |
| 14 | 在您的開發應用程式中，使用先前建立的GPX檔案切換位置。 | 您應該會看到根據先前設定的條件顯示應用程式內訊息。 |
| 15 | 在下一個測試中，我們基本上會複製與之前相同的步驟，但這次會測試本機通知。 | 預期的結果是每次符合符合條件時都會顯示本機通知。 |
| 16 | 設定新的應用程式內訊息（型別=廣播）。 |  |
| 16a | 在觸發器中，選取 **[!UICONTROL 地標事件型別]** - **[!UICONTROL 作為觸發器的專案]**. |  |
| 16b | 選取Places自訂中繼資料作為其他篩選器 — 使用 **[!UICONTROL POI型別]** = **[!UICONTROL 上次輸入的POI]**. |  |
| 16c | 選取自訂中繼資料索引鍵，協助您縮小將接收訊息的POI範圍。 |  |
| 16d | 對於頻率和持續時間，僅保留一或兩天，這樣如果您不喜歡該條件，可以在較短的時間內讓觸發程式過期。 |  |
| 16e | 對於永遠/一次或直到點進， **[!UICONTROL 一律]**. |  |
| 16f | 對於顯示型別，請選取 **[!UICONTROL 本機通知]**. |  |
| 16g | 準備/確認並部署應用程式內訊息。 |  |
| 17 | 在開發人員環境中，連線您的裝置並按下 **[!UICONTROL 播放]** 建置中。 建立位置正常運作後，請讓應用程式進入背景，並繼續在Xcode或Android Studio中切換位置。 您仍然應該會看到指出位置變更的主控台讀取，而且您應該也會看到根據觸發器中設定的條件而顯示的本機通知。 （可能有1-2秒的延遲。） | 預期的結果是每次符合相符條件時都會顯示本機通知。 |
|  | **摘要點** <br>在這個階段，我們應該會在本機環境中看到POI專案。 我們亦應根據POI運作方式檢視來自Campaign的傳訊。 如果失敗，請檢查Slack通知是否未發出。 如果沒有Slack訊息，請檢查應用程式主控台，因為可能尚未記錄新的位置專案。 如果結果成功，我們就能相當確定應用程式正確執行，且Places Service和Campaign傳訊服務也正常運作。 |  |
|  | **現場測試** <br>在位置上進行測試時，應該不會有多大變化。 讓Slack回傳保持作用中應該有助於瞭解裝置是否取得位置的進入和退出。 |  |
| 18 | 使用裝置進行測試，從WiFi和行動資料停用開始，然後在POI區域中啟用一次。 | 如果失敗，請記下您是否在Slack中取得地域範圍專案與通知。 Slack通知上的時間戳記為何？ |
| 19 | 執行測試時，僅啟用行動資料並關閉Wifi。 |  |
| 20 | 在行動電話及Wifi同時開啟的情況下進行測試。 |  |
|  | **摘要點** <br>現場測試應非常符合開發測試。 請記住，在決定使用者位置時，可能會有一些環境因素發揮效用，例如POI地理圍欄的逗留時間、儲存格訊號的可用性，以及附近WiFi存取點的強度。 |  |

## 記錄範例

**步驟8 ：** 位置更新期間的預期iOS和Android記錄

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**步驟9 ：** 事件期間的預期iOS和Android記錄

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
