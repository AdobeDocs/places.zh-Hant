---
title: 使用Places服務的應用程式內訊息
description: 本節提供如何以Campaign Standard方式使用推送訊息與以Campaign Standard方式使用應用程式內訊息的資訊。
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# 使用Places服務的應用程式內傳訊 {#in-app-messages-loc-service}

此資訊可協助您了解如何使用Places服務資訊來傳送應用程式內訊息或本機通知。

## 先決條件

開始之前，請完成下列工作：

* 已使用Adobe Experience Platform Mobile SDK設定行動應用程式，包括 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* 整合 [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 進入您的應用程式。
* 新增 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 設定。

* [建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md) （在「Places服務POI」管理介面中）。

* 安裝並設定 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md) 和區域監控解決方案([CoreLocation檔案](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) 針對iOS，或 [Android位置檔案](https://developer.android.com/training/location/geofencing))。

## 根據地理圍欄項目或退出傳送應用程式內訊息

1. 在您的Adobe Campaign Standard例項中，按一下 **[!UICONTROL 建立應用程式內訊息]**.
1. 對於訊息類型，請選取 **[!UICONTROL 鎖定行動應用程式的所有使用者]**.
1. 按一下 **[!UICONTROL 下一個]** 並輸入一般詳細資訊。
1. 在左窗格中，確認您可以使用與Places服務相關的各種觸發器。

   * 如果使用者已輸入POI地域欄位，您可以選擇顯示應用程式內訊息。
   * 您也可以使用Places服務UI中定義的中繼資料來篩選對象。

   在以下範例中，您可以觸發應用程式內訊息，該訊息只會顯示給進入其中一個度假勝地、且正在參加免費飲品計畫的使用者，而您想要在這些使用者抵達時向他們傳送優惠券。

   ![&quot;應用程式內訊息放置中繼資料&quot;](/help/assets/last-entered-vacation.png)

1. 按一下 **[!UICONTROL 下一個]** 完成建立傳遞的應用程式內訊息。

   ![&quot;建立事件&quot;](/help/assets/prepare-ACS.png)

   若要測試應用程式內訊息傳送，請在Xcode或Android Studio中啟動應用程式，並使用位置模擬器來選取符合訊息准則的POI。

   ![&quot;飲用券&quot;](/help/assets/drink-coupon-on-app.png)

搭配Adobe Campaign Standard使用Places Services提供強大的工具，讓您根據地理圍欄的進入和退出，將訊息分段及鎖定給使用者。 此整合可讓您建立更個人化和情境式的使用案例。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location Service with Campaign Messaging](https://www.youtube.com/watch?v=ikiTTQw9c-o)
