---
title: 搭配Adobe Campaign Standard使用地標
seo-title: 搭配Adobe Campaign Standard使用地標
description: 深入瞭解客戶偏好和習慣是成功行銷宣傳的關鍵。 瞭解使用者是否曾造訪過實體位置，也可以在與消費者建立關係時加入一些非常有價值的內容。
seo-description: 深入瞭解客戶偏好和習慣是成功行銷宣傳的關鍵。 瞭解使用者是否曾造訪過實體位置，也可以在與消費者建立關係時加入一些非常有價值的內容。
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# 搭配Adobe Campaign Standard使用地標 {#places-with-acs}

*感謝您上週造訪我們，我們很想讓您在下次造訪時獲得驚喜！*

深入瞭解客戶偏好和習慣是成功行銷宣傳的關鍵。 使用者搜尋的項目和先前的購買記錄在受眾定位中扮演了重要角色。 瞭解使用者是否曾造訪過實體位置，也可以在與消費者建立關係時加入一些非常有價值的內容。

根據eMarketer最近的一份報告，85%的高績效零售商認為，地點對於他們的行銷工作非常重要。 此外，北美地區超過58%的零售商都計畫投資鄰近地區／地點技術，以增強客戶體驗。

![](/help/assets/using-loc-services-acs_0.png)

請考慮智慧型手機使用體驗中的關鍵位置。 你的智慧手機多常會去附近的餐館、加油站、雜貨店或其他服務。

因此，身為品牌，您應該思考如何將位置運用在行銷宣傳中。 在本指南中，我們將說明您如何運用Adobe Experience Platform Experience Platform Location service的強大功能，透過Adobe Campaign Standard將位置內容新增至訊息，讓您根據歷史興趣點(POI)項目發佈個人化推播通知或應用程式內訊息。

在我們開始之前，本指南假設您有行動應用程式已設定Adobe Experience Platform Mobile SDK，且具備Adobe Campaign Standard擴充功能。 除了Adobe Experience Platform Mobile SDK和Campaign Standard外，您還應該能夠存取Experience Platform Location Service。

## 必要條件

1. 將 [Adobe Experience Platform Mobile SDK整合至您的應用程式](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
1. 將 [Adobe Campaign Standard Extension新增至您的行動應用程式設定](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。
1. [建立一或多個POI](/help/places-database-management-1/managing-pois-in-the-places-ui.md)。

>[!TIP]
>
>如果您正在尋找大量上傳或管理POI的方式，請檢視此指令 [碼，從CSV檔案上傳POI](https://github.com/adobe/places-scripts) 。 此外， [Places API](/help/places-rest-apis/api-usage/api-usage.md) 可用來建立或管理興趣點。

如果您沒有「地標」的存取權，您可以在此 [處申請存取權](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)。

### 在您的應用程式中啟用並安裝Places擴充功能

在「置入」介面中建立興趣點後，您需要將「置入」功能新增至應用程式。

1. 請依照指示，在您的應用程式中啟用「位置和位置」監視擴充功能。
1. 在「地標」延伸模組中，請確定您已選取先前建立之POI的適當資料庫。

   您隨時可以將其他程式庫新增至擴充功能設定。

1. 請確定您已將這些組態新增至程式庫，並在Launch中發佈組態變更。
1. 在「 **[UICONTROL Launch environments]** 」標籤中，按一下安裝指示圖示，以檢視有關將適當的CocoaPod和Gradle檔案下載至您的應用程式專案的指示。
1. 在您的應用程式中，請依照將「位置」背景模式新增至應用程式的指示，並啟動「位置位置監視器」。
1. 透過裝置模擬器測試您的應用程式，以根據欺騙裝置位置，在興趣點附近查看應用程式要求。

### 在Experience Platform Launch中建立資料元素

在您確認您的應用程式中的「位置」和「位置」監控擴充功能正常運作後，請在Experience Platform Launch中建立資料元素，以讀取擴充功能提供並透過Mobile SDK事件中樞提供的資訊。 資料元素實際上是別名，可從用戶端應用程式擷取資料。 讓我們建立一些資料元素，以從「地標」擴充功能擷取資料。

1. 在您的Experience Platform Launch mobile屬性中，按一下標籤 **[!UICONTROL Data Elements]** 上的並按一下 **[!UICONTROL Add Data Element]**。
1. 從擴展菜單中，選擇 **[!UICONTROL Places]**。
1. 從下拉 **[!UICONTROL Data Element]** 清單中，選擇 **[!UICONCONTROL名稱}**。
1. 在右側的窗口中，可以選 **[!UICONTROL Current POI]** 擇將檢索用戶當前所在的POI的名稱。

   * **[!UICONTROL Last Entered]** 檢索用戶上次輸入的POI的名稱
   * **[!UICONTROL Last Exited]** 將提供用戶最後左側的POI的名稱。

1. 選擇 **[!UICONTROL Last Entered]**.
1. 輸入資料元素的名稱，例如， **[!UICONTROL Last Entered POI Name]**&#x200B;然後按一下 **[!UICONTROL Save]**。


   ![](/help/assets/using-loc-services-acs_1.png)

1. 重複上述步驟，並為「上次輸入POI Latitude *」、「上次輸入POI經度*」、「上次輸入POI Radius」建立資料元素 ****。

除了Places的資料元素外，請確定您也已為 *App ID和* Experience Cloud ID建立Mobile Core **&#x200B;資料元素。

### 建立規則以傳送位置資料至Adobe Campaign Standard

Experience Platform Launch的規則可讓您根據事件觸發程式建立複雜的多解決方案工作流程。 您可以建立新規則或變更現有規則，並將更新動態部署至行動應用程式。 在此範例中，我們將建立在使用者進入地理圍欄的POI時觸發的規則。 觸發規則後，會傳送更新至Campaign Standard，以記錄使用者的特定POI項目。 此POI以Experience Cloud ID為基礎。

1. 在您的Experience Platform Launch mobile屬性中，按一下標籤 **[!UICONTROL Rules]** 並按一下 **[!UICONTROL Add Rule]**。
1. 在區段 **[!UICONTROL Events]** 中，按一下 **[!UICONTROL +]** 並選取 **[!UICONTROL Places]**。
1. 在中 **[!UICONTROL Event Type]**，選擇 **[!UICONTROL Enter POI]**。
1. 輸入規則的名稱，例如 **[!UICONTROL User entered POI]**。
1. 按一下 **[!UICONTROL Keep Changes]**。
1. 將部分保 **[!UICONTROL Conditions]** 留為空白。

   此區段可讓您篩選或限制觸發此規則的時間。

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. 在中 **[!UICONTROL Extension]**，選 **[!UICONTROL Mobile Core]** 擇並在中 **[!UICONTROL Action Type]**&#x200B;選擇 **[!UICONTROL Send Postback]**。

1. 對於URL，您需要建構您的Campaign Standard位置端點。

   URL看起來應類似下方的URL。 請務必使用您先前為促銷活動伺服器和pKey建立的正確資料元素。

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. 按一下方塊以新增貼文內文並傳送下列內容：

   ```text
   {
   "locationData": {
   "distances": "{%%Last Entered POI Radius%%}",
   "poiLabel": "{%%Last Entered POI Name%%}",
   "latitude": "{%%Last Entered POI Lat%%}",
   "longitude": "{%%Last Entered POI Long%%}",
   "appId": "{%%AppID%%}",
   "marketingCloudId": “{%%ecid%%}”
   }
   }
   ```

1. 使用您在上一節中建立的特定資料元素。
1. 在中 **[!UICONTROL Content Type]**&#x200B;鍵入 **[!UICONTROL application/json]**。
1. 設定 **[!UICONTROL Keep Changes]** 完此設定後按一下。

   設定Slack web鈎子作為額外動作，以驗證我的動作是否被觸發，以及是否收集了正確的資料，可能會有所幫助。

   >[!IMPORTANT]
   >
   >請記得將最近的變更發佈至您的應用程式，以確定規則和所有資料元素都已部署為您設定的一部分。 發佈後，您應重新啟動行動應用程式，以取得最新的組態更新。

### 使用位置資料來定位促銷活動標準訊息

既然我們在Campaign中填入了位置資料，我們就可以將興趣點當做受眾細分工具。

1. 在您的Adobe Campaign standard例項內，按一下「 **[UICONTROL建立推播通知」]**。
1. 對於推播通知類型，請選取「 **[UICONTROL傳送推播給應用程式訂閱者」]**。

   此推播類型將針對您應用程式的所有使用者。 如果您的行動使用者已附加至促銷活動描述檔，您也可以選取「 **[UICONCONTROL傳送推播至促銷活動描述檔]** i」。

1. 按一 **[!UICONTROL Next]** 下，然後在下一個畫面上輸入一般詳細資訊。
1. 在「對象」畫面上，按一 **[!UICONTROL Count]** 下以查看推播通知的預估傳送使用者人數。

   在此情況下，計數為3，因為測試應用程式上已安裝3個裝置。

1. 在左側邊欄上，展開標 **[!UICONTROL Profile]** 簽並拖曳主要區 **[!UICONTROL POI location]** 域上的篩選器。
1. 在「POI篩選器」窗口中，輸入要定位的POI的確切名稱。

   您可以進行其他選擇，以決定自使用者上次造訪此POI以來的時間範圍。

   ![](/help/assets/using-loc-services-acs_2.png)

1. 按一下 [!**UICONCONTROL確認]**。
1. 再次在頂端執行計數，以查看您的受眾規模變更。

   如果您未看到計數更新，則可能已輸入POI名稱，但沒有設備觸發該條目。 在這裡，使用Slack web掛接變得很有價值，因為您可以看到來自各種測試設備的POI條目清單。
1. 您可以拖曳其他POI位置篩選器，將多個POI加入訊息中。
1. 按一 **[!UICONTROL Next]** 下以完成建立傳送的推播通知。

   ![](/help/assets/using-loc-services-acs_3.png)

除了推播通知外，您也可以使用位置資料來區隔您想要接收應用程式內訊息的使用者。

1. 在您的Adobe Campaign standard例項中，按一下 **[!UICONTROL Create In-App message]**。
1. 對於消息類型，請選擇 **[!UICONTROL Target all users of a Mobile application]**。
1. 按一 **[!UICONTROL Next]** 下，然後在下一個畫面上輸入一般詳細資訊。
1. 在左窗格中，確認您現在可以使用與「地標」相關的各種觸發器。
1. 如果使用者已輸入POI地理圍欄，您可以選擇顯示應用程式內訊息。

   您也可以使用在「位置」UI中定義的中繼資料來篩選對象。 在此範例中，我想觸發應用程式內訊息，只顯示給上次退出POI且也有健身設施的使用者。 也許我想給他們發一份調查，看看他們是否使用／喜歡健身房。

1. 按一 **[!UICONTROL Next]** 下以完成建立應用程式內訊息的傳送。

   ![](/help/assets/using-loc-services-acs_4.png)

搭配使用Adobe Campaign Standard的「地標」為您提供功能強大的工具，讓您根據歷史位置來劃分訊息並將訊息鎖定給使用者。 此簡單的整合為建立更個人化和情境化的使用案例開啟了大門。

我們不斷改善「地標」和整合式解決方案，將位置相關內容帶入行動工作流程。 即將推出的Triggered Journey解決方案是一項將運用Places的產品，可讓客戶根據事件觸發因素（例如位置）建立即時工作流程。

## 建議的連結

如需詳細資訊，請參閱下列：

* [Adobe Experience Location Service](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard](https://www.adobe.com/marketing/campaign.html)
* [註冊以存取Adobe Places測試版](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)
* [Adobe Campaign與Experience Platform SDK整合](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
