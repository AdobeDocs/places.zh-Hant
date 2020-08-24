---
title: 測試和驗證Places服務
description: 本節提供如何測試和驗證Places服務的資訊。
translation-type: tm+mt
source-git-commit: 954bd9a12ede841d189138dfbe3d65ad4c1bd3c3
workflow-type: tm+mt
source-wordcount: '1735'
ht-degree: 2%

---


# 測試地點服務的建議 {#test-validate-loc-svc}

許多客戶和組織將定義全球範圍內的POI，因此，有一種方法來模擬和測試Places Service如何與您的應用程式互動非常重要。 這些資訊可協助您瞭解如何測試和驗證根據已定義的POI和使用者目前位置正確觸發的Places Service登入與退出點。

由於環境變數可能是位置訊號和準確度的因素，因此我們建議您先使用開發人員工具和模擬位置項目，在本機建立基準結果。 其目標是驗證所有位置事件皆正確運作。 在正確驗證位置事件後，可測試解決方案整合（例如Analytics、Target和Campaign）。 為協助您的測試活動，您應在個別開發環境中設定Slack Webhook，並加上回傳並載入GPX檔案。

>[!IMPORTANT]
>
>此計畫假設已在 [Places Service UI中建立POI](https://places.adobe.com) ，且已安裝並正確設定Places擴充功能和Places Monitor擴充功能的最新版本。 如需詳細資訊，請參 [閱「放置擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md) 」 [和「放置監視器擴充功能](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)」。

| 步驟 ： | 說明 | 預期結果 |
|--- |--- |--- |
| 1 | 確認已為Android輸入正確的資訊清單金鑰，以授與追蹤位置的存取權。 如需詳細資訊，請參 [閱新增資訊清單權限](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest)。 | 已確認 |
| 1a | 確認iOS中已設定位置更新。 此外，請確定您已在iOS中設定適當的plist金鑰，以要求使用者追蹤位置的權限。 如需詳細資訊，請 [參閱在背景啟用位置更新。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | 已確認 |
| 2 | 確認為iOS設定了哪個監控模式。 連續模式允許更高的準確性和持久性，同時也允許更大的耗電量。 如需詳細資訊，請參 [閱監視模式（僅限iOS）。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | 重大變更或持續 |
| 3 | 如果使用多個POI程式庫，請確認已在Experience Platform Launch的Places擴充功能中選取了適當的程式庫。 | 已確認 |
| 4 | 確認最新版的Mobile Core和Places/Places Monitor擴充功能已透過Gradle或CocoaPods與應用程式搭售。 | 已確認——如需最近更新的詳細資訊，請參閱版 [本說明。](/help/release-notes.md) |
| 5 | 確認已為測試配置了正確的環境。 啟動環境ID應符合您的啟動開發環境。 | 已確認 |
| 6 | 為您要測試的每個POI建立GPX檔案。 GPX檔案可用於本機開發環境，以模擬位置項目。 如需有關建立和使用GPX檔案的詳細資訊，請參閱： <br>[行動應用程式中iOS模擬器的GPX](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[檔案[已關閉] https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION測試](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX檔案會建立並載入應用程式專案中。 |
| 7 | 不需執行其他動作，您應能夠從Android Studio或XCode啟動應用程式，並檢視適當的警報以要求追蹤位置的存取權。 按一下「 *永遠允許* 」權限。<br><br>我們建議您使用連接至電腦的實際裝置，而非使用裝置模擬器。 | 在通過IDE載入的應用程式上應顯示位置請求提示 |
| 8 | 接受「位置」權限後。 Places SDK將擷取裝置的目前位置，而Places Monitor擴充功能將開始從目前位置監視最近20個POI | 請參見表下的日誌示例。 |
| 9 | 在XCode或Android Studio中的不同位置之間切換時，應針對特定POI產生登入事件。 進入POI時，應使用以下日誌。 | 請參見表下的日誌示例。 |
| 10 | 在您看到Places Monitor找到附近的POI後，您應該通過發送位置ping來測試。 在Launch中，建立新規則，使用Places擴充功能根據地理圍欄項目觸發。 然後使用Mobile Core來傳送回傳，以建立新動作。 建立Slack Webhook應用程式可協助您查看位置登入和退出點。 如需有關建立Slack Webhook應用程式的詳細資訊，請參閱「使 [用傳入的Webhook傳送訊息」。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 在Launch中，請確定您已新增「地標」擴充功能的資料元素，包括： <br>當前POI名當前POI<br>latCurrent POI<br>latLast Extived退出當前POI<br>latLongPoi<br><br><br><br><br><br>latLast Lat退出Oract Lat退出OratLatExtimestamp |  |
| 10b | 使用「事件=地點」→「輸入POI」建立新規則 |  |
| 10c | 建立動作=行動核心→回傳 |  |
| 10d | 使用Slack應用程式的Webhook URL，例如https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | 員額內容類似： `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>請確定您使用此處建立的特定資料元素。 |  |
| 10f | 請確定您在Launch中發佈所有新資料元素和規則變更。 （您應在Launch介面的右上方選取工作開發程式庫。） |  |
| 11 | 在開發人員IDE中切換GPX位置，以再次啟動並測試您的應用程式。 | 您現在在開發環境中選擇不同位置時，應會看到Slack通知，顯示每個POI的登入點。 |
|  | **快速摘**<br>&#x200B;要點此測試的所有內容都可在本機執行，而不需前往特定的POI位置。 驗證測試有助於確保您的應用程式已正確設定，且已收到正確的位置權限。 <br><br>此驗證也可讓您確信已定義的POI可以正確使用Places Monitor擴充功能。  在此步驟後，我們將開始測試Campaign中的訊息，以檢視是否根據POI登入和退出顯示正確的訊息。 |  |
|  | **使用Places服務測試Adobe Campaign Standard應用程式內訊息。** |  |
| 12 | 在主「促銷活動」控制面板上，設定新的「應用程式內訊息」（類型= broadcast） |  |
| 12a | 在觸發器中，選 **擇置入事件類型——輸入作為觸發器**。 |  |
| 12b | 選 **[!UICONTROL Places Custom metadata]** 擇作為其他篩選器——使用POI類型=上次輸入的POI。<br>我們使 **[!UICONTROL Last Entered]** 用POI類型，因為在大多數情況 **[!UICONTROL Last Entered]** 下，會與相同 **[!UICONTROL Current POI]**。 <br><br>**[!UICONTROL Current POI]**只能用於POI地域圍欄重疊的情況。 在這種情況下，這些POI必須是「排名」,**[!UICONTROL Current POI]**然後在使用者目前可能在的2或3個地理圍欄中，顯示排名最前的POI。 |  |
| 12c | 選取自訂中繼資料金鑰，協助您縮小將會收到訊息的POI。 |  |
| 12d | 在頻率和持續時間上，請只保留一或兩天，如此，如果您不喜歡標準，則可在較短的時間內使觸發器過期。 |  |
| 12e | 對於「永遠／一次」或「直到點進」，請選取「永 *遠* 」，以便您可以跨多個位置進行測試。 | 當您模擬符合適當中繼資料條件的位置變更時，應用程式內訊息會一律顯示。 |
| 12f | 對於顯示，請選擇「本機通知」以外的選項。 這樣，在前景中使用應用程式進行測試時，就更容易看到。) |  |
| 12g | 準備／確認並部署應用程式內訊息。 |  |
| 13 | 在您的開發環境中，為確保已下載新的促銷活動規則，請結束並再次啟動應用程式。 | 請勿忘記，新的促銷活動規則檔案必須重新完整啟動應用程式，才能下載至裝置。 |
| 14 | 在您的開發應用程式中，使用先前建立的GPX檔案來切換位置。 | 您應該會根據先前設定的准則，看到應用程式內訊息出現。 |
| 15 | 在下次測試中，我們基本上會複製與以前相同的步驟，但這次我們將測試LOCAL NOTIFICATION。 | 預期結果是，每次符合符合標準時，就會顯示本機通知。 |
| 16 | 設定新的應用程式內訊息（類型= broadcast）。 |  |
| 16a | 在觸發器中，選擇 **[!UICONTROL Places event type]** - **[!UICONTROL Entry as the trigger]**。 |  |
| 16b | 選取「置入自訂中繼資料」作為其他篩選條件——使 **[!UICONTROL POI type]** 用= **[!UICONTROL Last Entered POI]**。 |  |
| 16c | 選取自訂中繼資料金鑰，協助您縮小將會收到訊息的POI。 |  |
| 16d | 對於頻率和持續時間，請只保留一或兩天，如此，如果您不喜歡標準，則可在較短的時間內使觸發器過期。 |  |
| 16e | 對於「永遠／一次」或「直到點進」 **[!UICONTROL ALWAYS]**。 |  |
| 16f | 對於顯示類型，選擇 **[!UICONTROL Local Notification]**。 |  |
| 16g | 準備／確認並部署應用程式內訊息。 |  |
| 17 | 在開發人員環境中，連接您的裝置並按 **[!UICONTROL Play]** 建置版本。 在您建立該位置運作後，請在應用程式背景設定，並繼續在Xcode或Android Studio中切換位置。 您仍應看到指示位置變更的主控台讀出畫面，而且您也應看到顯示的本機通知，視觸發器中設定的標準而定。 （可能會有1-2秒的延遲。） | 預期結果是，每次符合符合符合標準時，就會顯示本機通知。 |
|  | **摘要** ：在 <br>此階段，我們應該看到本地環境中的POI條目。 我們也應該會根據POI工作，看到Campaign傳送的訊息。 如果出現故障，請檢查Slack通知是否未發出。 如果沒有Slack消息，請檢查應用程式控制台，因為可能沒有記錄新位置條目。 如果結果成功，我們可以相當確定應用程式是否正常運作，以及Places Service和Campaign傳訊服務是否也正常運作。 |  |
|  | **現場測試** ：在 <br>位置測試時，應該不會有太大改變。 保持鬆弛回傳活動有助於瞭解設備是否進入和退出該位置。 |  |
| 18 | 在裝置上進行測試，先停用wifi和行動電話，然後在POI區啟用一次。 | 如果發生故障，請記住是否在Slack中獲得地理圍欄條目和通知。 Slack通知的時間戳記是什麼？ |
| 19 | 只要啟用蜂窩功能，並關閉wifi，即可進行測試。 |  |
| 20 | 開啟行動電話和wifi時進行測試。 |  |
|  | **SUMMARY POINT** 現 <br>場測試應與開發測試緊密相配。 請記住，在決定使用者位置時，有一些環境因素可發揮作用，例如POI地理圍欄逗留時間、儲存格訊號的可用性，以及附近wifi接入點的強度。 |  |

## 日誌示例

**步驟8:** 在位置更新期間需要iOS和Android記錄檔

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**步驟9:** 事件期間需要iOS和Android記錄檔

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
