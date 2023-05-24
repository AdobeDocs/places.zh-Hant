---
title: 使用Places服務的推播通知
description: 本節提供如何在Campaign Standard中使用Places服務與推播通知的相關資訊。
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 4%

---

# 使用Places服務的推播通知 {#push-notifications}

在本節中，您將瞭解如何使用歷史地理位置資訊來鎖定透過Adobe Campaign Standard傳送的推播通知。

## 先決條件

開始之前，請先完成下列工作：

* 行動應用程式已設定為Adobe Experience Platform Mobile SDK，包括 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* 整合 [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 放入您的應用程式中。
* 新增 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 至您的行動應用程式設定。

* [建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md) 在Places服務POI管理介面中。

* 啟用並安裝 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## 在Experience Platform Launch中建立資料元素

驗證Places擴充功能和區域監控解決方案後([CoreLocation檔案](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) 適用於iOS，或 [Android位置檔案](https://developer.android.com/training/location/geofencing))可在您的應用程式中正常運作，您需要在Experience Platform Launch中建立資料元素。 資料元素可讓您讀取來自Mobile SDK事件中樞之擴充功能所提供的資訊，並作為別名從使用者端應用程式擷取資料。 若要從Places擴充功能擷取資料，並將Places Service資訊傳送至Campaign，您需要建立一些資料元素。

建立資料元素的方式:

1. 在您的Experience Platform Launch行動屬性中，按一下 **[!UICONTROL 資料元素]** 標籤並按一下 **[!UICONTROL 新增資料元素]**.
1. 在 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL Places Service]**.
1. 從 **[!UICONTROL 資料元素型別]** 下拉式清單，選取 **[!UICONTROL 名稱]**.
1. 在右側窗格中，您可以選取 **[!UICONTROL 目前的POI]** ，會擷取使用者目前所在的POI名稱。

   **[!UICONTROL 上次輸入]** 擷取使用者上次輸入的POI名稱，並且 **[!UICONTROL 上次退出]** 提供使用者最後離開的POI名稱。 在此範例中，我們選取 **[!UICONTROL 上次輸入]** 並輸入資料元素的名稱，例如 **[!UICONTROL 上次輸入的POI名稱]** 並按一下 **[!UICONTROL 儲存]**.

   ![「Campaign Standard中的推播訊息」](/help/assets/ACS_Push1.png)

1. 重複上述步驟1-4並建立資料元素 *上次進入的POI緯度*， *上次輸入的POI經度*、和 *上次輸入的POI半徑*.

除了Places Service的資料元素之外，請確定您建立的行動核心資料元素 *應用程式ID* 和 *EXPERIENCE CLOUDID*.

## 建立規則以將位置資料傳送至Adobe Campaign Standard

Experience Platform Launch中的規則可讓您根據事件觸發器建立複雜的多解決方案工作流程。 透過規則，您可以建立新規則或修改現有規則，並將更新動態部署至您的行動應用程式。 在以下範例中，當使用者輸入地理圍欄式POI時，就會觸發規則。 觸發規則後，系統會傳送更新給Campaign Standard，以根據Experience CloudID記錄特定使用者之特定POI的專案。

1. 在您的Experience Platform Launch行動屬性中，於 **[!UICONTROL 規則]** 標籤，按一下 **[!UICONTROL 新增規則]**.
1. 在 **[!UICONTROL 事件]** 區段，按一下 **[!UICONTROL +]** 並選取 **[!UICONTROL Places Service]** 作為擴充功能。
1. 對於 **[!UICONTROL 事件型別]**，選取 **[!UICONTROL 輸入POI]**.
1. 為規則命名，例如， **使用者輸入的POI**.
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.
1. 離開 **[!UICONTROL 條件]** 區段空白。

   此區段可讓您篩選或限制此規則觸發的時間。

1. 在 **[!UICONTROL 動作]** 區段，按一下 **[!UICONTROL +]**.
1. 在 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 行動核心]** 和 **[!UICONTROL 動作型別]** 下拉式清單，選取 **[!UICONTROL 傳送回傳]**.
1. 在 **[!UICONTROL URL]**，您需要建構Campaign Standard位置端點。

   URL應類似於 `https:///rest/head/mobileAppV5//locations/`.
確保您使用先前為Campaign伺服器和pKey建立的正確資料元素。

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

1. 請務必使用您在上一節中建立的資料元素。
1. 在&#x200B;**[!UICONTROL 「內容類型」]**&#x200B;中，輸入 **[!UICONTROL application/json]**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

>[!IMPORTANT]
>
>* 將SlackWeb連結設定為其他動作，以驗證是否正在觸發專案，以及是否正在收集正確的資料可能會有幫助。
>* 請記得將最近的變更發佈至應用程式，以確定規則和所有資料元素都會部署為設定的一部分。 發佈後，請再次啟動行動應用程式以取得最新的設定更新。


## 使用位置資料來鎖定促銷活動訊息

現在我們已在Campaign中填入位置資料，接下來可以使用POI作為對象區段工具。

1. 在您的Adobe Campaign Standard執行個體中，按一下 **[!UICONTROL 建立推播通知]**.
1. 對於推播通知型別，請選取「 」 **[!UICONTROL 傳送推播至Campaign設定檔]**.
1. 按一下 **[!UICONTROL 下一個]** 並輸入一般詳細資訊。
1. 在「對象」畫面上，按一下 **[!UICONTROL 計數]** 以判斷將會傳送推播通知的估計使用者人數。

   >[!TIP]
   >
   >在此範例中，計數將為3，因為有三個已安裝裝置正在測試應用程式。

1. 在左窗格中，展開 **[!UICONTROL 設定檔]** 定位並拖曳 **[!UICONTROL POI位置]** 篩選至主要區域。
1. 在POI篩選視窗中，輸入您要鎖定的POI的確切名稱。

   >[!TIP]
   >
   >您可以進行其他選擇以確定自使用者上次造訪此POI以來的時間段。

   ![「ACS中的推播訊息2」](/help/assets/ACS_push2.png)

1. 按一下「**[!UICONTROL 確認]**」。
1. 在頂端再次執行計數，以檢視您的對象人數變化。

   如果您沒有看到計數更新，表示您可能輸入的POI名稱沒有任何裝置觸發專案。 在這種情況下，擁有SlackWeb鉤點會變得很有價值，因為您可以看到來自各種測試裝置的POI專案清單。

1. 您可以拖曳出其他POI位置篩選器，以便在訊息中包含多個POI。
1. 按一下&#x200B;**[!UICONTROL 「下一步」]**&#x200B;完成建立傳遞的推送通知。

   ![「ACS中的推播訊息3」](/help/assets/ACS_push3.png)

搭配Adobe Campaign Standard使用Places Service可讓您使用強大工具，根據地理圍欄進入和退出，針對使用者細分及鎖定傳訊。 此整合可協助您建立更個人化和情境式的使用案例。
