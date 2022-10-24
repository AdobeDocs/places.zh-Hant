---
title: Places服務的推播通知
description: 本節提供如何在Places Service中搭配推播通知使用Campaign Standard的相關資訊。
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 4%

---

# Places服務的推播通知 {#push-notifications}

在本節中，您將學習如何使用歷史地理位置資訊來定位透過Adobe Campaign Standard傳送的推播通知。

## 先決條件

開始之前，請完成下列工作：

* 已使用Adobe Experience Platform Mobile SDK設定行動應用程式，包括 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* 整合 [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 進入您的應用程式。
* 新增 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 設定。

* [建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md) （在「Places服務POI」管理介面中）。

* 啟用並安裝 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## 在Experience Platform Launch中建立資料元素

在驗證Places擴充功能和地區監控解決方案後([CoreLocation檔案](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) 針對iOS，或 [Android位置檔案](https://developer.android.com/training/location/geofencing))在應用程式中正常運作，您必須在Experience Platform Launch中建立資料元素。 資料元素可讓您讀取來自Mobile SDK事件中樞的擴充功能所提供的資訊，並做為別名，以從用戶端應用程式擷取資料。 若要從Places擴充功能擷取資料，並將Places服務資訊傳送至Campaign，您需要建立一些資料元素。

建立資料元素的方式:

1. 在您的Experience Platform Launch行動屬性中，按一下 **[!UICONTROL 資料元素]** 按一下 **[!UICONTROL 新增資料元素]**.
1. 在 **[!UICONTROL 擴充功能]** 下拉清單，選擇 **[!UICONTROL Places Service]**.
1. 從 **[!UICONTROL 資料元素類型]** 下拉清單，選擇 **[!UICONTROL 名稱]**.
1. 在右側窗格中，您可以選取 **[!UICONTROL 目前POI]** 會擷取使用者目前所在之POI的名稱。

   **[!UICONTROL 上次輸入]** 擷取使用者上次輸入的POI名稱，並 **[!UICONTROL 上次退出]** 提供使用者最後一個離開的POI名稱。 在此範例中，我們選取 **[!UICONTROL 上次輸入]** 並輸入資料元素的名稱，例如 **[!UICONTROL 上次輸入的POI名稱]** 點按 **[!UICONTROL 儲存]**.

   ![&quot;Campaign Standard中的推送訊息&quot;](/help/assets/ACS_Push1.png)

1. 重複上述步驟1至4，並為 *上次輸入的POI緯度*, *上次輸入的POI經度*，和 *上次輸入的POI半徑*.

除了Places Service的資料元素外，請務必為 *應用程式ID* 和 *Experience CloudID*.

## 建立規則以將位置資料傳送至Adobe Campaign Standard

Experience Platform Launch中的規則可讓您根據事件觸發器建立複雜的多重解決方案工作流程。 使用規則，您可以建立新規則或修改現有規則，並將更新動態部署至行動應用程式。 在下列範例中，當使用者進入地理圍欄POI時，就會觸發規則。 觸發規則後，會傳送更新給Campaign Standard，以根據Experience CloudID記錄特定使用者的特定POI項目。

1. 在您的Experience Platform Launch行動屬性中， **[!UICONTROL 規則]** 按一下 **[!UICONTROL 新增規則]**.
1. 在 **[!UICONTROL 事件]** ，按一下 **[!UICONTROL +]** 選取 **[!UICONTROL Places Service]** 作為擴充功能。
1. 若 **[!UICONTROL 事件類型]**，選取 **[!UICONTROL 輸入POI]**.
1. 為規則命名，例如 **使用者輸入的POI**.
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.
1. 保留 **[!UICONTROL 條件]** 區段空白。

   本節可讓您篩選或限制何時應觸發此規則。

1. 在 **[!UICONTROL 動作]** ，按一下 **[!UICONTROL +]**.
1. 在 **[!UICONTROL 擴充功能]** 下拉清單，選擇 **[!UICONTROL 行動核心]** 和 **[!UICONTROL 動作類型]** 下拉清單，選擇 **[!UICONTROL 傳送回傳]**.
1. 在 **[!UICONTROL URL]**，您需要建構Campaign Standard位置端點。

   URL看起來應類似 `https:///rest/head/mobileAppV5//locations/`.
請確定您使用先前為Campaign伺服器和pKey建立的正確資料元素。

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
1. 在&#x200B;**[!UICONTROL 「內容類型」]**&#x200B;中，輸入 **[!UICONTROL application/json]**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

>[!IMPORTANT]
>
>* 將SlackWeb連結設定為額外動作，以驗證是否已觸發登入且正在收集正確資料，可能會有所幫助。
>* 請記得將最近的變更發佈至您的應用程式，以確定規則和所有資料元素已部署為設定的一部分。 發佈後，請再次啟動行動應用程式以取得最新的設定更新。


## 使用位置資料來定位促銷活動訊息

現在，Campaign中已填入位置資料，我們可以將POI作為受眾區段工具。

1. 在您的Adobe Campaign Standard例項中，按一下 **[!UICONTROL 建立推播通知]**.
1. 針對推播通知類型，請選取 **[!UICONTROL 傳送推送至Campaign設定檔]**.
1. 按一下 **[!UICONTROL 下一個]** 並輸入一般詳細資訊。
1. 在「對象」畫面上，按一下 **[!UICONTROL 計數]** 以決定推播通知的預計傳送使用者數。

   >[!TIP]
   >
   >在此示例中，計數為3，因為有三台已安裝的設備正在測試應用程式。

1. 在左窗格中，展開 **[!UICONTROL 設定檔]** 標籤並拖曳 **[!UICONTROL POI位置]** 篩選至主區域。
1. 在「POI篩選」視窗中，輸入您要鎖定的POI的確切名稱。

   >[!TIP]
   >
   >您可以進行其他選取，以判斷使用者上次造訪此POI後的時段。

   ![&quot;ACS中的推送訊息2&quot;](/help/assets/ACS_push2.png)

1. 按一下 **[!UICONTROL 確認]**.
1. 在頂端再次執行計數，以查看對象大小變更。

   如果您沒有看到計數更新，表示您可能已輸入POI名稱，但沒有任何裝置觸發此項目。 在此情況下，擁有SlackWeb連結會很有價值，因為您可以看到來自各種測試裝置的POI項目清單。

1. 您可以拖出其他POI位置篩選器，在訊息中包含多個POI。
1. 按一下&#x200B;**[!UICONTROL 「下一步」]**&#x200B;完成建立傳遞的推送通知。

   ![&quot;ACS中的推送訊息3&quot;](/help/assets/ACS_push3.png)

搭配Adobe Campaign Standard使用Places Service提供強大的工具，讓您根據地理圍欄的進入和退出點，將訊息分段及鎖定給使用者。 此整合可協助您建立更個人化和情境式的使用案例。
