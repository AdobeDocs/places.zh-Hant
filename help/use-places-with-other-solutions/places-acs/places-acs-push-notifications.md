---
title: 推播通知
seo-title: 推播通知
description: 本節提供如何在Campaign Standard中搭配推播通知使用「地標」的相關資訊。
seo-description: '本節提供如何在Campaign Standard中搭配推播通知使用「地標」的相關資訊。 '
translation-type: tm+mt
source-git-commit: 4ee8adb73f6dec15030a160c27edbeca71d3507b

---


# 含位置服務的推播通知 {#push-notifications}

在本指南中，我們將說明您如何使用歷史地理位置資訊來定位透過Adobe Campaign standard傳送的推播通知。

## 必要條件

開始之前，請完成下列工作：

* 使用Adobe Experience Platform Mobile SDK設定行動應用程式，包括 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 將 [Adobe Experience Platform Mobile SDK整合至您的應用程式](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
* 將 [Adobe Campaign Standard Extension新增至您的行動應用程式設定](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。

* [在「地標](/help/poi-mgmt-ui/create-a-poi-ui.md) 」 POI管理介面中建立POI。

* 啟用並安裝 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)。


## 在Experience Platform Launch中建立資料元素

在您確認Places and Places Monitor for Location Service擴充功能在應用程式中運作正常後，請在Experience Platform Launch中建立資料元素。 資料元素可讓您讀取透過Mobile SDK事件中樞提供之擴充功能所提供的資訊，並當成別名，從用戶端應用程式擷取資料。 若要從「位置」擴充功能擷取資料並將「位置」資訊傳送至Campaign，您需要建立一些資料元素。

要建立資料元素：

1. 在您的Experience Platform Launch mobile屬性中，按一下標籤， **[!UICONTROL Data Elements]** 然後按一下「 **[!UICONTROLA新增資料元素」]**。
1. 在下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Places]**。
1. 從下拉 **[!UICONTROL Data Element Type]** 式清單中，選取 **[!UICONTROL Name]**。
1. 在右側窗格中，可以選 **[!UICONTROL Current POI]** 擇檢索用戶當前所在的POI名稱的用戶。

   **[!UICONTROL Last Entered]** 檢索用戶上次輸入的POI的名稱， **[!UICONTROL Last Exited]** 並提供用戶最後左側的POI的名稱。 在此範例中，我們將選取 **[!UICONTROL Last Entered]** 並輸入資料元素的名稱，例如並 **[!UICONTROL Last Entered POI Name]** 按一下 **[!UICONTROL Save]**。

   !["Campaign Standard中的推送訊息"](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

除了位置服務的資料元素外，請確定您已為應用程式ID和 *Experience Cloud ID建立Mobile Core**資料元素*。

## 建立規則以傳送位置資料至Adobe Campaign Standard

Experience Platform Launch的規則可讓您根據事件觸發程式建立複雜、多解決方案的工作流程。 有了規則，您可以建立新規則或修改現有規則，並將更新動態部署至行動應用程式。 在下列範例中，當使用者進入地理圍欄的POI時，將會觸發規則。 觸發規則後，會傳送更新至Campaign Standard，以根據Experience Cloud ID記錄特定使用者的特定POI項目。

1. 在您的Launch mobile屬性中，按一 **[!UICONTROL Rules]** 下索引標籤 **[!UICONTROL Add Rule]**。
1. 在區段 **[!UICONTROL Events]** 下，按一 **[!UICONTROL +]** 下並選 **[!UICONTROL Places]** 取為延伸模組。
1. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
1. 為規則命名，例如，用戶 **輸入POI**。
1. 按一下 **[!UICONTROL Keep Changes]**。
1. 將部分保 **[!UICONTROL Conditions]** 留為空白。

   此區段可讓您篩選或限制觸發此規則的時間。

1. 在區段 **[!UICONTROL Actions]** 下，按一下 **[!UICONTROL +]**。
1. 在下拉 **[!UICONTROL Extension]** 式清單中，選 **[!UICONTROL Mobile Core]** 取並在下 **[!UICONTROL Action Type]** 拉式清單中選取 **[!UICONTROL Send Postback]**。
1. 在中 **[!UICONTROL URL]**，您需要建構您的Campaign standard位置端點。

   URL看起來應類似 `https:///rest/head/mobileAppV5//locations/`。
請確定您使用先前為促銷活動伺服器和PKey建立的正確資料元素。

1. 按一下方塊以新增貼文內文並傳送下列內容：

   ```
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

1. 請確定您使用在上一節中建立的資料元素。
1. 在中 **[!UICONTROL Content Type]**&#x200B;鍵入 **[!UICONTROL application/json]**。
1. 按一下 **[!UICONTROL Keep Changes]**。

>[!IMPORTANT]
>
>* 設定Slack web掛接，以驗證項目是否被觸發以及收集正確資料，可能會有所幫助。


>* 請記得將最近的變更發佈至您的應用程式，以確定規則和所有資料元素都已部署為您設定的一部分。 發佈後，您應再次啟動行動應用程式，以取得最新的組態更新。


## 使用位置資料來定位促銷活動訊息

既然我們在Campaign中填入了位置資料，我們就可以將POI當成觀眾區隔工具。

1. 在您的Adobe Campaign standard例項中，按一下 **[!UICONTROL Create Push Notification]**。
1. 對於推播通知類型，請選取 **[!UICONTROL Send push to Campaign profiles]**。
1. 按一 **[!UICONTROL Next]** 下並輸入一般詳細資訊。
1. 在「對象」畫面上，按 **[!UICONTROL Count]** 一下以決定推播通知的預估傳送使用者數。

   >[!TIP]
   >
   >在此範例中，計數為3，因為有3個已安裝的裝置正在測試應用程式。

1. 在左窗格中，展開標 **[!UICONTROL Profile]** 簽並拖曳篩 **[!UICONTROL POI location]** 選器至主要區域。
1. 在「POI篩選」視窗中，輸入您要定位的POI的確切名稱。

   >[!TIP]
   >
   >您可以進行其他選擇，以決定自使用者上次造訪此POI以來的時段。

   !["ACS中的推送消息2"](/help/assets/ACS_push2.png)

1. 按一下 **[!UICONTROL Confirm]**。
1. 再次在頂端執行計數，以查看您的受眾規模變更。

   如果您未看到計數更新，則可能已輸入POI名稱，但沒有設備觸發了該條目。 在這種情況下，使用Slack web掛接變得很有價值，因為您可以看到來自各種測試設備的POI條目清單。
1. 您可以拖曳其他POI位置篩選器，將多個POI加入訊息中。
1. Click **[!UICONTROL Next]** to finish creating the push notification for delivery.

   !["ACS中的推送消息3"](/help/assets/ACS_push3.html)

搭配使用Adobe Campaign standard的位置服務為您提供強大的工具，讓您根據地理圍欄登入和退出點，將訊息分段並定位給使用者。 此整合可協助您建立更個人化和情境化的使用案例。