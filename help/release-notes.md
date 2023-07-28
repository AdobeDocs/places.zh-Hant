---
title: 發行說明
description: Places Service發行說明。
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 2%

---

# 發行說明 {#release-notes}

## 2020 年 7 月 8 日

* **Places和Places監視擴充功能**

   * 已新增Places和Places監視擴充功能 [React原生應用程式](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * 已新增Places和Places監視擴充功能 [Cordova應用程式](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * 如需詳細資訊，請參閱： [使用Places擴充功能](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 2020年5月12日

* **Places Service**

   * 使用「匯入POI」按鈕，從CSV檔案大量匯入POI
   * 選取多個POI並大量編輯或新增中繼資料值

## 2020年5月6日

* **PlacesMonitor 2.2.1**

   * **Android**

      * 改善的記錄

## 2020 年 5 月 5 日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * 改善的記錄

## 2020 年 2 月 20 日

* **ACPPlaces 1.3.1 (iOS)**

   * Places擴充功能現在會在核心SDK中向事件中樞報告版本資訊。
   * 裝置POI會籍資訊的預設存留時間是從收集到現在起的一小時。 如需詳細資訊，請參閱 [修改Places成員資格存留時間](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * Places擴充功能現在會在核心SDK中向事件中樞報告版本資訊。
   * 裝置POI會籍資訊的預設存留時間是從收集到現在起的一小時。 如需詳細資訊，請參閱 [修改Places成員資格存留時間](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日

* **PlacesMonitor 2.2.0**

   * **Android**

      * 呼叫新的Places API以在應用程式啟動和應用程式執行時和授權變更時收集位置授權狀態。
      * 新增setRequestLocationPermission API及已廢止的setLocationPermission API。

## 2020 年 1 月 9 日

* **Places 1.4.0**

   * **Android**

      * 新增API、 `setAuthorizationStatus`，以設定Places服務的裝置授權狀態。 值會儲存並用於Places共用狀態。

## 2019年12月4日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * 呼叫Places API以在裝置變更時從裝置收集CLAuthorizationStatus。

## 2019年12月3日

* **ACPPlaces 1.3.0**

   * **iOS**

      * 新增API、 `setAuthorizationStatus`，以設定Places服務的裝置授權狀態。 值會儲存並用於Places共用狀態。

## 2019 年 11 月 25 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 修正使用多個Pod專案選項的Cocoapod專案匯入陳述式。

## 2019年11月22

* **PlacesMonitor 2.1.1**

   * **Android**

      * 監視器現在會辨識Android裝置的開機，並視需要根據裝置目前的位置再次向作業系統登入地理圍欄。
      * 修正有時會捨棄登入/退出事件的競爭條件。

## 2019 年 9 月 10 日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 新增API、 `setRequestAuthorizationLevel`，以設定會提示使用者的位置授權要求型別。


   * **Android**

      * 新增API、 `setLocationPermission`，以設定會提示使用者的位置許可權要求型別。
      * Places監視現在支援Android 10。

## 2019 年 8 月 8 日

此版本已進行下列更新：

### UI更新

以下為Places UI的更新清單：

#### 新功能

* 新增清單檢視，顯示沒有地圖的POI。
* 針對城市、州/省、國家/地區和中繼資料新增POI篩選選項。
* 組織中的第一個程式庫會自動建立。
* 新增POI排序至清單檢視。

#### UI更新

* 將清單和詳細資料面板移至UI右側。
* 已在UI頂端新增搜尋面板。
* 如果只有一個程式庫存在，當您建立POI時，系統會自動選取此程式庫。
* 將程式庫管理移至快顯視窗。
* 在篩選器旁新增POI計數。

## 2019 年 8 月 6 日

此版本已進行下列更新：

### 監視Launch Extension 2.0.0

* 更新Places監視2.0的Android和iOS安裝指示。

## 2019 年 7 月 31 日

此版本已進行下列更新：

### Places監視2.0.0

* 監視狀態現在會在啟動之間持續存在。
* 處理因位置許可權要求而產生的回呼時，不再需要您擴充PlacesActivity。
* 變更現有API，讓開發人員可從裝置清除所有Places資料：

  舊API： `public static void stop();`

  新API： `public static void stop (final boolean clearData);`

* 更新使用 `getNearbyPointsOfInterest` API可更有效地處理錯誤案例。

## 2019 年 7 月 25 日

此版本已進行下列更新：

### ACPPlacesMonitor 2.0.0

* 若要清除裝置中的所有Places資料，

  在ACPPlacesMonitor中，取代現有的API `+ (void) stop;` 替換為`+ (void) stop: (BOOL) clearData;`.

* 更新ACPlaces的使用 `getNearbyPointsOfInterest` API可更有效地處理錯誤案例。

## 2019 年 7 月 22 日

此版本已進行下列更新：

### Android Places 1.3.0

* 新增API，可從共用狀態、應用程式內記憶體和共用偏好設定中清除所有Places相關資料。
* 修正應用程式啟動期間未更新共用狀態的問題。
* 修正以下錯誤： `getNearbyPointsOfInterest` 回呼傳回錯誤碼 `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` 沒有網際網路。
* `getNearbyPointsOfInterest` API （沒有errorCallback）將具有 `successCallback` 使用空白的poi清單呼叫，以防擷取附近的地標時發生錯誤。

## 2019 年 7 月 19 日

此版本已進行下列更新：

**iOS Places 1.2.0**

新增API以清除共用狀態、應用程式內記憶體和 `NSUserDefaults`.

## 2019年6月25日

此版本已進行下列更新：

**iOS Places監視1.0.2**

* 改善生活品質，包括更出色的程式碼內檔案和記錄。

## 2019年6月17日

此版本已進行下列更新：

**iOS Places 1.1.0**

* 已新增新的API，以便在擷取附近地標時發生失敗時傳回錯誤代碼。
* 當隱私權狀態變更為選擇退出時，所有與Places相關的資料現在將從裝置上清除。
* 修正在首次啟動後，由於網路狀況不佳，有時導致Places事件遺失的問題。
* 修正了連續快速處理POI專案事件時，透過規則引擎進行的權杖取代有時會參考不正確POI的問題。

## 2019 年 5 月 30 日

**Android Places監視器1.0.1**

* 修正當Places監視啟動時，導致POI無法進入事件的問題。

## 2019 年 5 月 28 日

修正Places使用者介面中的下列問題：

* 更新「地點」的解決方案切換器，使其與Experience Cloud其餘部分一致。
* 修正在未進行排名變更的情況下儲存排名的問題。
* 將UI中允許的最小半徑增加至10米。
* 修正如果您刪除欄位中的所有數字，半徑欄位會重設回20米的問題。

## 2019年5月17日

此版本已進行下列更新：

**Android Places 1.2.0**

* 新增API以處理個別地理圍欄。
* 進行錯誤修正，以防止多個連續進入事件。

**Android Places監視器1.0.0**

適用於Android的Places監視的初始版本。

Places監視會管理作業系統層級Location API，並直接與Places擴充功能通訊。 安裝這兩個擴充功能後，客戶的應用程式就能立即監控區域。
如需Places監視器的詳細資訊，請按一下這裡。


## 2019年5月2日

**Android Places 1.1.0**

* 推出適用於getNearByPlaces的新API，此API具有errorCallback，且呼叫時帶有errorCode，指出錯誤原因。
* Places擴充功能現在會將事件排入佇列，直到取得設定為止。
* 新增環境感知設定的支援。
* 錯誤修正：修正區域登入/退出事件的索引鍵
* 最後已知位置的儲存現在會適當尊重使用者的隱私權狀態


## 2019 年 4 月 9 日

此版本已進行下列更新：

**iOS Places監視1.0.1**

* 新增完整單位測試涵蓋範圍。
* CI整合(CircleCI)
* 程式碼涵蓋範圍整合(codecov)

## 2019年3月25

iOS Places監視器1.0.0

適用於iOS的Places監視的初始版本。

Places監視會管理作業系統層級Location API，並直接與Places擴充功能通訊。 安裝這兩個擴充功能後，客戶的應用程式就能立即監控區域。

## 2019 年 2 月 28 日

### 測試版本

這是Places Service的第一個版本，這套工具可讓客戶透過真實世界的位置資料來豐富其使用者體驗。 在第一個版本中，我們的主要使用案例是讓行動應用程式擷取自訂位置資料，並透過Adobe Experience Platform Launch對該資料採取行動。

### 主要功能

以下是此版本的主要功能：

#### Places Service UI

我們已發佈管理UI，您可在其中檢視及管理地標(POI)。 您也可以將POI整理至程式庫中。 除了標準中繼資料（例如城市、州和類別）之外，我們也支援將自訂中繼資料新增到POI的功能。

* 若要檢視UI，請前往 [https://places.adobe.com](https://places.adobe.com).
* 若要開始使用UI，請參閱 [快速入門](/help/getting-started.md).

#### Places擴充功能

使用Places擴充功能，您可以將Places服務程式庫新增至行動應用程式，並對其POI採取行動。 使用Experience Platform Launch中的規則產生器，您便可以在使用者進入和退出POI時觸發動作，以利觸發。

在Places擴充功能中：

* 您可以選擇要納入應用程式的POI資料庫。
* 在POI登入或退出時觸發的規則事件。
* 建立指向使用者目前POI的資料元素。

如需Places擴充功能的詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places API

您可以使用Places API來執行下列動作：

* 允許開發人員填入及更新其POI清單。
* 建置您自己的UI或整合現有的POI資料庫。
* 使用Places API批次端點來大量匯入POI。

  您可以使用隨附的Python公用程式完成大量匯入。

如需Places API的詳細資訊，請參閱 [網站服務API](/help/web-service-api/places-web-services.md).

### 即將推出

#### Analytics 整合

正在更新Analytics擴充功能，以在使用者處於POI （被動呼叫）時，自動將位置內容資料從Places Service資料庫新增至所有傳出的Analytics呼叫。 此更新也將允許建立規則，以便直接在POI進入或退出（作用中呼叫）時引發Analytics追蹤呼叫。
