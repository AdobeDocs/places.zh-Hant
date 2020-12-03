---
title: 發行說明
description: Places服務的發行說明。
translation-type: tm+mt
source-git-commit: 3f986697179eb9c0af1d9b54daf67793a99b8491
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 3%

---


# 發行說明 {#release-notes}

## 2020 年 7 月 8 日

* **Places and Places Monitor Extensions**

   * 已為React Native應用程式新增Places和Places Monitor [擴充功能](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * 已為 [Cordova應用程式新增「位置」和「位置」監控擴充功能](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * 如需詳細資訊，請參閱： [使用Places延伸功能](https://docs.adobe.com/content/help/zh-Hant/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 2020 年 5 月 12 日

* **Places Service**

   * 使用「匯入POI」按鈕，從CSV檔案大量匯入POI
   * 選取多個POI並大量編輯或新增中繼資料值

## 2020 年 5 月 6 日

* **PlacesMonitor 2.1.1**

   * **Android**

      * 改善的記錄功能

## 2020 年 5 月 5 日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * 改善的記錄功能

## 2020 年 2 月 20 日

* **ACPPlaces 1.3.1(iOS)**

   * 現在，放置擴充功能會將版本資訊報告至核心SDK中的事件中心。
   * 裝置POI會籍資訊目前的預設上線時間為收集後一小時。 如需詳細資訊，請 [參閱修改地點會籍的上線時間](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1(Android)**

   * 現在，放置擴充功能會將版本資訊報告至核心SDK中的事件中心。
   * 裝置POI會籍資訊目前的預設上線時間為收集後一小時。 如需詳細資訊，請 [參閱修改地點會籍的上線時間](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日

* **PlacesMonitor 2.2.0**

   * **Android**

      * 呼叫新的Places API，以收集應用程式啟動時和應用程式執行時授權變更的位置授權狀態。
      * 已新增setRequestLocationPermission API和已過時的setLocationPermission API。

## 2020 年 1 月 9 日

* **Places 1.4.0**

   * **Android**

      * 已新增新API, `setAuthorizationStatus`以設定Places Services的裝置授權狀態。 值會儲存並用於「位置」共用狀態。

## 2019 年 12 月 4 日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * 呼叫Places API，在裝置變更時從裝置收集CLAuthorizationStatus。

## 2019 年 12 月 3 日

* **ACPPlaces 1.3.0**

   * **iOS**

      * 已新增新API, `setAuthorizationStatus`以設定Places Services的裝置授權狀態。 值會儲存並用於「位置」共用狀態。

## 2019 年 11 月 25 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 修正使用多個pod專案選項的Cocoapods專案匯入陳述式。

## 2019 年 11 月 22 日

* **PlacesMonitor 2.1.1**

   * **Android**

      * 監視器現在會辨識Android裝置的啟動，並視需要根據裝置的目前位置，在作業系統中重新註冊地理柵欄。
      * 修正有時會導致登入／退出事件被捨棄的競賽條件。

## 2019年10月9日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 已新增新API, `setRequestAuthorizationLevel`以設定將提示使用者的位置授權要求類型。
   * **Android**

      * 新增新API, `setLocationPermission`以設定將提示使用者的位置權限要求類型。
      * Places Monitor現在支援Android 10。



## 2019 年 8 月 8 日

此版本已進行下列更新：

### UI更新

以下是Places UI的更新清單：

#### 新功能

* 已新增清單檢視，顯示不含地圖的POI。
* 新增城市、州、國家和中繼資料的POI篩選選項。
* 系統會自動建立組織中的第一個資料庫。
* 已將POI排序新增至「清單檢視」。

#### UI更新

* 將清單和詳細資訊面板移至UI的右側。
* 新增搜尋面板至UI頂端。
* 如果只有一個庫存在，則建立POI時會自動選擇此庫。
* 將程式庫管理移至快顯視窗。
* 在篩選器旁新增POI計數。

## 2019 年 8 月 6 日

此版本已進行下列更新：

### 螢幕啟動擴充功能2.0.0

* 已更新Places Monitor 2.0的Android和iOS安裝指示。

## 2019 年 7 月 31 日

此版本已進行下列更新：

### Places Monitor 2.0.0

* 監控狀態現在會在啟動之間持續存在。
* 回呼的處理（由位置權限要求產生）不再需要您擴充PlacesActivity。
* 已變更現有的API，讓開發人員可從裝置清除所有Places資料：

   舊API: `public static void stop();`

   New API: `public static void stop (final boolean clearData);`

* 更新API的使用 `getNearbyPointsOfInterest` ，以更有效率地處理錯誤案例。

## 2019 年 7 月 25 日

此版本已進行下列更新：

### ACPPlacesMonitor 2.0.0

* 要清除設備中的所有「位置」資料，

   在ACPPlacesMonitor中，將現有的API取代 `+ (void) stop;` 為`+ (void) stop: (BOOL) clearData;`。

* 更新ACPPlaces `getNearbyPointsOfInterest` API的使用，以更有效率地處理錯誤案例。

## 2019 年 7 月 22 日

此版本已進行下列更新：

### Android Places 1.3.0

* 已新增API，可清除共用狀態、應用程式內記憶體和共用偏好設定中所有與位置相關的資料。
* 已修正在應用程式啟動期間，共用狀態未更新的問題。
* 已修正回呼在無 `getNearbyPointsOfInterest` 網際網路上傳回錯誤 `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` 代碼的錯誤。
* `getNearbyPointsOfInterest` API（不含errorCallback）將會以空 `successCallback` 白的poi清單呼叫，以防擷取附近的地標時出錯。

## 2019 年 7 月 19 日

此版本已進行下列更新：

**iOS Places 1.2.0**

已新增API，可清除共用狀態、應用程式內記憶體和所有與Places相關的資料 `NSUserDefaults`。

## 2019 年 6 月 25 日

此版本已進行下列更新：

**iOS Places Monitor 1.0.2**

* 改善生活品質，包括更佳的程式碼內檔案和記錄。

## 2019 年 6 月 17 日

此版本已進行下列更新：

**iOS Places 1.1.0**

* 已新增新API，以在擷取附近位置時傳回錯誤碼。
* 當隱私權狀態變更為選擇退出時，所有與地點相關的資料現在都會從裝置上擦除。
* 修正首次啟動後，有時會因網路狀況不佳而遺失「地標」事件的問題。
* 修正在快速接續處理POI項目事件時，透過規則引擎取代代號有時會參照錯誤POI的問題。

## 2019 年 5 月 30 日

**Android Places Monitor 1.0.1**

* 修正當「位置」監控啟動時，POI無法進入事件的問題。

## 2019 年 5 月 28 日

已修正「地標」UI中的下列問題：

* 更新Places中的Solution Switcher，使其與Experience Cloud的其他部分一致。
* 修正在未進行排名變更的例項中儲存排名的問題。
* 將UI中允許的最小半徑提高至10米。
* 修正如果刪除欄位中的所有數字，半徑欄位會重設回20米的問題。

## 2019 年 5 月 17 日

此版本已進行下列更新：

**Android Places 1.2.0**

* 已新增API以處理個別Geofence。
* 錯誤修正，以防止多個連續的登入事件。

**Android Places Monitor 1.0.0**

Places Monitor for Android的初始版本。

Places Monitor會管理作業系統層級的位置API，並直接與Places擴充功能通訊。 在安裝這兩個擴充功能後，客戶就可以在其應用程式中進行立即可用的區域監控。
有關「Places Monitor（位置監視器）」的詳細資訊，請按一下這裡。


## 2019 年 5 月 2 日

**Android Places 1.1.0**

* 引入getNearByPlaces的新API，其中包含errorCallback，並以errorCode呼叫，指出錯誤的原因。
* Places擴充功能現在會將事件排入佇列，直到取得設定為止。
* 新增對環境感知組態的支援。
* 錯誤修正：更正了區域進入／退出事件的鍵
* 儲存最後一個已知位置現在會正確遵守使用者的隱私權狀態


## 2019 年 4 月 9 日

此版本已進行下列更新：

**iOS Places Monitor 1.0.1**

* 已新增完整單元測試涵蓋範圍。
* CI整合(CircleCI)
* 程式碼涵蓋範圍整合(codecov)

## 2019 年 3 月 25 日

iOS Places Monitor 1.0.0

iOS版Places Monitor的初始發行。

Places Monitor會管理作業系統層級的位置API，並直接與Places擴充功能通訊。 在安裝這兩個擴充功能後，客戶就可以在其應用程式中進行立即可用的區域監控。 有關Places Monitor的詳細資訊，請參 [閱Places Monitor擴展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

## 2019 年 2 月 28 日

### 測試版

這是Places Service的第一版。Places Service是一套工具，可讓客戶運用實際位置資料豐富其使用者的體驗。 在第一版中，我們的主要使用案例是讓行動應用程式能夠擷取自訂位置資料，並透過Adobe Experience Platform Launch對該資料採取行動。

### 主要功能

以下是此版本的主要功能：

#### Places Service UI

我們已發佈管理UI，您可在其中檢視及管理興趣點(POI)。 您也可以將POI組織到資料庫。 除了標準中繼資料（例如城市、州和類別）外，我們也支援將自訂中繼資料新增至POI的能力。

* 若要檢視UI，請前往https://places.adobe.com [](https://places.adobe.com)。
* 若要開始使用UI，請參閱快 [速入門](/help/getting-started.md)。

#### Places擴充功能

使用Places Extension，您可以將您的Places Service程式庫新增至行動應用程式，並依其POI採取行動。 使用Experience Platform Launch中的規則產生器，您可以在使用者進入並退出POI時觸發動作。

在「地標」擴充功能中：

* 您可以選擇應用程式中要包含的POI程式庫。
* 在POI進入或退出時觸發的規則事件。
* 建立指向使用者目前POI的資料元素。

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### 地標API

您可以使用Places API執行下列作業：

* 允許開發人員填入並更新其POI清單。
* 建立您自己的UI或與現有POI資料庫整合。
* 使用「置入API」批次端點來大量匯入POI。

   您可以使用提供的Python實用程式完成批量導入。

如需Places API的詳細資訊，請參閱 [Web service API](/help/web-service-api/places-web-services.md)。

### 即將推出

#### Analytics 整合

Analytics擴充功能正在更新，當使用者在POI（被動呼叫）中時，會自動從Places Service資料庫將位置上下文資料新增至所有傳出的Analytics呼叫。 此更新也可讓規則建立在POI登入或退出（作用中呼叫）處直接觸發Analytics追蹤呼叫。
