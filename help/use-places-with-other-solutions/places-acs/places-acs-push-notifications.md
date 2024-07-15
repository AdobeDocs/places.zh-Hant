---
title: 使用Places服務的推播通知
description: 本節提供如何在Campaign Standard中使用Places服務搭配推播通知的資訊。
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# 使用Places服務的推播通知 {#push-notifications}

在本節中，您將瞭解如何使用歷史地理位置資訊來將透過Adobe Campaign Standard傳送的推播通知設為目標。

## 先決條件

開始之前，請先完成下列工作：

* 擁有以Adobe Experience Platform Mobile SDK設定的行動應用程式，包括[Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 將[Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)整合至您的應用程式。
* 將[Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)新增至您的行動應用程式設定。

* [在Places Service POI管理介面中建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。

* 啟用並安裝[Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)。


## 在Experience Platform Launch中建立資料元素

驗證Places擴充功能和區域監視解決方案([iOS的CoreLocation檔案](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions)，或[Android位置檔案](https://developer.android.com/training/location/geofencing))在您的應用程式中正常運作後，您需要在Experience Platform Launch中建立資料元素。 資料元素可讓您讀取透過行動SDK事件中樞的擴充功能所提供的資訊，並作為別名來擷取使用者端應用程式的資料。 若要從Places擴充功能擷取資料，並將Places服務資訊傳送至Campaign，您需要建立一些資料元素。

若要建立資料元素：

1. 在您的Experience Platform Launch行動屬性中，按一下&#x200B;**[!UICONTROL 資料元素]**&#x200B;索引標籤，然後按一下&#x200B;**[!UICONTROL 新增資料元素]**。
1. 在&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL Places服務]**。
1. 從&#x200B;**[!UICONTROL 資料元素型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 名稱]**。
1. 在右側窗格中，您可以選取&#x200B;**[!UICONTROL 目前的POI]**，以擷取使用者目前所在的POI名稱。

   **[!UICONTROL 上次進入時間]**&#x200B;會擷取使用者上次進入的POI名稱，而&#x200B;**[!UICONTROL 上次退出時間]**&#x200B;會提供使用者上次離開的POI名稱。 在此範例中，我們選取&#x200B;**[!UICONTROL 上次輸入]**&#x200B;並輸入資料元素的名稱，例如&#x200B;**[!UICONTROL 上次輸入的POI名稱]**，然後按一下&#x200B;**[!UICONTROL 儲存]**。

   ![「Campaign Standard中的推播訊息」](/help/assets/ACS_Push1.png)

1. 重複上述步驟1-4，並建立&#x200B;*上次進入的POI緯度*、*上次進入的POI經度*&#x200B;和&#x200B;*上次進入的POI半徑*&#x200B;的資料元素。

除了Places服務的資料元素之外，請確定您為&#x200B;*應用程式ID*&#x200B;和&#x200B;*Experience CloudID*&#x200B;建立行動核心資料元素。

## 建立規則以將位置資料傳送至Adobe Campaign Standard

Experience Platform Launch中的規則可讓您根據事件觸發器建立複雜的多解決方案工作流程。 透過規則，您可以建立新規則或修改現有規則，並將更新動態部署至您的行動應用程式。 在下列範例中，當使用者進入地理圍欄式POI時，就會觸發規則。 觸發規則後，系統會傳送更新給Campaign Standard，以根據Experience CloudID記錄特定使用者之特定POI的專案。

1. 在您的Experience Platform Launch行動屬性中，按一下&#x200B;**[!UICONTROL 規則]**&#x200B;標籤上的&#x200B;**[!UICONTROL 新增規則]**。
1. 在&#x200B;**[!UICONTROL Events]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL +]**&#x200B;並選取&#x200B;**[!UICONTROL Places Service]**&#x200B;做為延伸。
1. 針對&#x200B;**[!UICONTROL 事件型別]**，選取&#x200B;**[!UICONTROL 輸入POI]**。
1. 為規則命名，例如，**使用者輸入的POI**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**。
1. 將&#x200B;**[!UICONTROL 條件]**&#x200B;區段保留空白。

   此區段可讓您篩選或限制此規則應該引發的時間。

1. 在&#x200B;**[!UICONTROL 動作]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL +]**。
1. 在&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 行動核心]**，並在&#x200B;**[!UICONTROL 動作型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 傳送Postback]**。
1. 在&#x200B;**[!UICONTROL URL]**&#x200B;中，您需要建構您的Campaign Standard位置端點。

   URL應類似於`https:///rest/head/mobileAppV5//locations/`。
確保您使用先前為Campaign伺服器和pKey建立的正確資料元素。

1. 按一下方塊以新增貼文本文並傳送下列內容：

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

1. 務必使用您在上一節中建立的資料元素。
1. 在&#x200B;**[!UICONTROL 「內容類型」]**&#x200B;中，輸入 **[!UICONTROL application/json]**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

>[!IMPORTANT]
>
>* 將SlackWeb連結設定為其他動作以驗證是否正在觸發專案，以及是否正在收集正確的資料可能會有幫助。
>* 請記得將最近的變更發佈至應用程式，確認規則和所有資料元素都已部署為設定的一部分。 發佈後，請再次啟動行動應用程式以取得最新的設定更新。

## 使用位置資料以行銷活動訊息為目標

現在，我們已在Campaign中填入位置資料，我們可以使用POI作為對象區段工具。

1. 在您的Adobe Campaign Standard執行個體中，按一下&#x200B;**[!UICONTROL 建立推播通知]**。
1. 對於推播通知型別，請選取&#x200B;**[!UICONTROL 傳送推播至促銷活動設定檔]**。
1. 按一下「下一步」****&#x200B;並輸入一般詳細資料。
1. 在「對象」畫面上，按一下&#x200B;**[!UICONTROL 計數]**&#x200B;以決定將會傳送推播通知的估計使用者數目。

   >[!TIP]
   >
   >在此範例中，計數將為3，因為有三個已安裝的裝置正在測試應用程式。

1. 在左窗格中，展開&#x200B;**[!UICONTROL 設定檔]**&#x200B;標籤，並將&#x200B;**[!UICONTROL POI位置]**&#x200B;篩選器拖曳至主區域。
1. 在POI篩選視窗中，輸入您要鎖定之目標POI的確切名稱。

   >[!TIP]
   >
   >您可以進行其他選擇，以確定自使用者上次造訪此POI以來的時間段。

   ![「ACS中的推播訊息2」](/help/assets/ACS_push2.png)

1. 按一下「**[!UICONTROL 確認]**」。
1. 在頂端再次執行計數，以檢視您的對象人數變化。

   如果您沒有看到計數更新，表示您輸入的POI名稱可能沒有任何裝置觸發專案。 在此情況下，擁有SlackWeb勾點會變得很有價值，因為您可以看到來自各種測試裝置的POI專案清單。

1. 您可以拖曳出其他POI位置篩選器，以便在訊息中包含多個POI。
1. 按一下&#x200B;**[!UICONTROL 「下一步」]**&#x200B;完成建立傳遞的推送通知。

   ![「ACS中的推播訊息3」](/help/assets/ACS_push3.png)

搭配Adobe Campaign Standard使用Places Service可讓您使用強大工具，根據地理圍欄輸入和退出點將訊息分段並鎖定使用者。 此整合可協助您建立更個人化和情境式的使用案例。
