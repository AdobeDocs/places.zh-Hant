---
title: 使用Places Service的應用程式內訊息
description: 本節提供如何在Campaign Standard中將推送訊息與Campaign Standard中的應用程式內訊息搭配使用的相關資訊。
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# 使用Places服務的應用程式內傳訊 {#in-app-messages-loc-service}

此資訊可協助您瞭解如何使用Places服務資訊來傳送應用程式內訊息或本機通知。

## 先決條件

開始之前，請先完成下列工作：

* 擁有以Adobe Experience Platform Mobile SDK設定的行動應用程式，包括[Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 將[Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)整合至您的應用程式。
* 將[Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)新增至您的行動應用程式設定。

* [在Places Service POI管理介面中建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。

* 在您的行動應用程式中安裝並設定[Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)和區域監視解決方案([iOS的CoreLocation檔案](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions)，或[Android位置檔案](https://developer.android.com/training/location/geofencing))。

## 根據地域範圍登入或退出傳送應用程式內訊息

1. 在您的Adobe Campaign Standard執行個體中，按一下&#x200B;**[!UICONTROL 建立應用程式內訊息]**。
1. 針對訊息型別，選取&#x200B;**[!UICONTROL 將行動應用程式的所有使用者設為目標]**。
1. 按一下「下一步」**&#x200B;**&#x200B;並輸入一般詳細資料。
1. 在左窗格中，確認您可以使用與Places服務相關的各種觸發器。

   * 如果使用者已輸入POI地理範圍，您可以選擇顯示應用程式內訊息。
   * 您也可以使用Places Services使用者介面中定義的中繼資料來篩選對象。

   在下列範例中，您可以觸發應用程式內訊息，此訊息僅會向輸入免費飲品方案其中一個度假勝地的使用者顯示，而您想要在這些使用者抵達時傳送優惠券。

   ![「應用程式內訊息放置中繼資料」](/help/assets/last-entered-vacation.png)

1. 按一下&#x200B;**[!UICONTROL 下一步]**&#x200B;完成建立傳遞的應用程式內訊息。

   ![&quot;建立事件&quot;](/help/assets/prepare-ACS.png)

   若要測試應用程式內訊息傳送，請在Xcode或Android Studio中啟動應用程式，並使用位置模擬器來選取符合訊息傳送條件的POI。

   ![「飲料優惠券」](/help/assets/drink-coupon-on-app.png)

搭配Adobe Campaign Standard使用Places Services可讓您根據地理圍欄進入和退出，針對使用者細分及鎖定訊息。 此整合可讓您建立更個人化和情境式的使用案例。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

使用Campaign傳訊的[Adobe Experience Platform定位服務](https://www.youtube.com/watch?v=ikiTTQw9c-o)
