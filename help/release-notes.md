---
title: 發行說明
description: Places Service的發行說明。
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 3%

---

# 發行說明 {#release-notes}

## 2020 年 7 月 8 日

* **Places and Places監視擴展**

   * 已為新增「Places and Places監視」擴充功能 [React本機應用程式](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * 已為新增「Places and Places監視」擴充功能 [科爾多瓦應用程式](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * 如需詳細資訊，請參閱： [使用Places擴充功能](https://docs.adobe.com/content/help/zh-Hant/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 2020年5月12日

* **Places Service**

   * 使用「匯入POI」按鈕，從CSV檔案大量匯入POI
   * 選取多個POI並大量編輯或新增中繼資料值

## 2020年5月6日

* **PlacesMonitor 2.2.1**

   * **Android**

      * 改善記錄

## 2020 年 5 月 5 日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * 改善記錄

## 2020 年 2 月 20 日

* **ACPPlaces 1.3.1(iOS)**

   * Places擴充功能現在會將版本資訊報告至核心SDK的事件中心。
   * 裝置POI成員資訊現在具有預設的上線時間，從收集到該資訊之時算起一小時。 如需詳細資訊，請參閱 [修改Places成員資格的存留時間](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1(Android)**

   * Places擴充功能現在會將版本資訊報告至核心SDK的事件中心。
   * 裝置POI成員資訊現在具有預設的上線時間，從收集到該資訊之時算起一小時。 如需詳細資訊，請參閱 [修改Places成員資格的存留時間](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日

* **PlacesMonitor 2.2.0**

   * **Android**

      * 呼叫新的Places API以在應用程式啟動時，以及應用程式執行時授權變更時收集位置授權狀態。
      * 已新增setRequestLocationPermission API和已棄用的setLocationPermission API。

## 2020 年 1 月 9 日

* **Places 1.4.0**

   * **Android**

      * 新增API, `setAuthorizationStatus`，以設定Places服務的裝置授權狀態。 值會儲存並用於Places共用狀態。

## 2019年12月4日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * 呼叫Places API以在變更時從裝置收集CLAuthorizationStatus。

## 2019年12月3日

* **ACPPlaces 1.3.0**

   * **iOS**

      * 新增API, `setAuthorizationStatus`，以設定Places服務的裝置授權狀態。 值會儲存並用於Places共用狀態。

## 2019 年 11 月 25 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 修正使用多個Pod專案選項的Cocoapods專案匯入陳述式。

## 2019 年 11 月 22 日

* **PlacesMonitor 2.1.1**

   * **Android**

      * 監視器現在會辨識Android裝置的啟動，並視需要根據裝置的目前位置，在作業系統中重新註冊地理柵欄。
      * 修正有時會捨棄登入/退出事件的競爭條件。

## 2019 年 9 月 10 日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 新增API, `setRequestAuthorizationLevel`，設定將提示用戶的位置授權請求類型。
   * **Android**

      * 新增API, `setLocationPermission`，以設定將提示使用者的位置權限請求類型。
      * Places監視器現在支援Android 10。



## 2019 年 8 月 8 日

此版本已進行下列更新：

### UI更新

以下是Places UI的更新清單：

#### 新功能

* 新增清單檢視，顯示沒有地圖的POI。
* 已新增城市、州、國家/地區和中繼資料的POI篩選選項。
* 系統會自動建立組織中的第一個程式庫。
* 將POI排序新增至清單檢視。

#### UI更新

* 將清單和詳細資訊面板移至UI的右側。
* 在UI頂端新增搜尋面板。
* 如果只有一個程式庫，當您建立POI時，就會自動選取此程式庫。
* 將程式庫管理移至快顯視窗。
* 在篩選器旁新增POI計數。

## 2019 年 8 月 6 日

此版本已進行下列更新：

### 監視器Launch擴充功能2.0.0

* 更新Places監視器2.0的Android和iOS安裝指示。

## 2019 年 7 月 31 日

此版本已進行下列更新：

### Places監視器2.0.0

* 監控狀態現在會在啟動之間持續存在。
* 處理回呼（由位置權限請求產生）不再需要您擴充PlacesActivity。
* 已變更現有API，讓開發人員可從裝置清除所有Places資料：

   舊API: `public static void stop();`

   新API: `public static void stop (final boolean clearData);`

* 更新 `getNearbyPointsOfInterest` API可更有效地處理錯誤情況。

## 2019年7月25日

此版本已進行下列更新：

### ACPPlacesMonitor 2.0.0

* 要清除設備中的所有Places資料，

   在ACPPlacesMonitor中，取代現有API `+ (void) stop;` with`+ (void) stop: (BOOL) clearData;`.

* 更新ACPPlace的使用 `getNearbyPointsOfInterest` API可更有效地處理錯誤情況。

## 2019 年 7 月 22 日

此版本已進行下列更新：

### Android Places 1.3.0

* 新增API，清除共用狀態、應用程式內記憶體和共用偏好設定中所有與Places相關的資料。
* 修正應用程式啟動期間未更新共用狀態的問題。
* 修正 `getNearbyPointsOfInterest` 回呼傳回錯誤程式碼 `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` 在網際網路上。
* `getNearbyPointsOfInterest` API（沒有errorCallback）會有 `successCallback` 以空poi清單呼叫，以防擷取附近的地標時發生錯誤。

## 2019年7月19日

此版本已進行下列更新：

**iOS Places 1.2.0**

新增API，清除共用狀態、應用程式內記憶體和 `NSUserDefaults`.

## 2019年6月25日

此版本已進行下列更新：

**iOS Places監視器1.0.2**

* 改善生命品質，包括改善程式碼內檔案和記錄功能。

## 2019年6月17日

此版本已進行下列更新：

**iOS Places 1.1.0**

* 新增API，以在擷取附近位置時傳回錯誤碼。
* 現在，當隱私權狀態變更為選擇退出時，所有與Places相關的資料都會從裝置上清除。
* 修正在首次啟動後，有時會因網路狀況不佳而遺失Places事件的問題。
* 修正快速連續處理POI登入事件時，透過規則引擎取代代號有時會參考錯誤POI的問題。

## 2019 年 5 月 30 日

**Android Places監視器1.0.1**

* 修正了在「位置」監視啟動時，無法為POI進入事件的問題。

## 2019 年 5 月 28 日

修正Places UI中的下列問題：

* 更新Places中的解決方案切換器，使其與其餘Experience Cloud一致。
* 修正在未進行排名變更的情況下會儲存排名的問題。
* 將UI中允許的最小半徑增加至10米。
* 修正如果刪除欄位中的所有數字，半徑欄位會重設為20米的問題。

## 2019年5月17日

此版本已進行下列更新：

**Android Places 1.2.0**

* 新增處理個別地理柵欄的新API。
* 防止多個連續登入事件的錯誤修正。

**Android Places監視器1.0.0**

Android適用的Places監視器初始發行。

「Places監視器」會管理作業系統層級的「位置API」，並直接與Places擴充功能通訊。 安裝兩個擴充功能後，客戶的應用程式中即可進行現成可用的地區監控。
有關「Places監視器」的詳細資訊，請按一下這裡。


## 2019年5月2日

**Android Places 1.1.0**

* 推出getNearByPlaces的新API，其含有errorCallback，且以指出錯誤原因的errorCode呼叫。
* Places擴充功能現在會讓事件進入佇列，直到取得設定為止。
* 新增對環境感知設定的支援。
* 錯誤修正：已更正區域進入/退出事件的鍵
* 儲存最後一個已知位置現在會正確遵守使用者的隱私權狀態


## 2019 年 4 月 9 日

此版本已進行下列更新：

**iOS Places監視器1.0.1**

* 已新增完整單元測試涵蓋範圍。
* CI整合(CircleCI)
* 代碼涵蓋範圍整合(codecov)

## 2019年3月25日

iOS Places監視器1.0.0

初次發行Places監視器for iOS。

「Places監視器」會管理作業系統層級的「位置API」，並直接與Places擴充功能通訊。 安裝兩個擴充功能後，客戶的應用程式中即可進行現成可用的地區監控。

## 2019 年 2 月 28 日

### 測試版

這是Places Service的第一版，這是一組工具，可讓客戶以真實世界的位置資料豐富其使用者的體驗。 在第一版中，我們的主要使用案例是讓行動應用程式能夠擷取自訂位置資料，並透過Adobe Experience Platform Launch對該資料採取行動。

### 主要功能

以下是此版本的主要功能：

#### Places服務UI

我們已發佈管理UI，您可在其中檢視及管理地標(POI)。 您也可以將POI整理到資料庫中。 除了城市、州和類別等標準中繼資料，我們也支援將自訂中繼資料新增至POI的功能。

* 若要查看UI，請前往 [https://places.adobe.com](https://places.adobe.com).
* 若要開始使用UI，請參閱 [快速入門](/help/getting-started.md).

#### Places擴充功能

使用Places擴充功能，您可以將Places Service資料庫新增至行動應用程式，並對其POI採取行動。 使用Experience Platform Launch中的規則產生器，您可以在使用者進入並退出POI時觸發動作。

在Places擴充功能中：

* 您可以選擇要在應用程式中加入的POI程式庫。
* 在POI登入或退出時觸發的規則事件。
* 建立指向使用者目前POI的資料元素。

如需Places擴充功能的詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places API

您可以使用Places API執行下列操作：

* 允許開發人員填入並更新其POI清單。
* 建立您自己的UI或與現有POI資料庫整合。
* 使用Places API批次端點來大量匯入POI。

   可以使用提供的Python實用程式完成批量導入。

如需Places API的詳細資訊，請參閱 [網站服務API](/help/web-service-api/places-web-services.md).

### 即將推出

#### Analytics 整合

正在更新Analytics擴充功能，以在使用者處於POI（被動呼叫）時，自動將位置內容資料從您的Places Service資料庫新增至所有傳出的Analytics呼叫。 此更新也可讓規則建立在POI項目或退出（作用中呼叫）時直接觸發Analytics追蹤呼叫。
