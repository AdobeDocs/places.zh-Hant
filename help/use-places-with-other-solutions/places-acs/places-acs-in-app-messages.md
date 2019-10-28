---
title: 包含位置服務的應用程式內訊息
seo-title: 包含位置服務的應用程式內訊息
description: 本節提供如何在Campaign Standard中搭配Campaign standard中的應用程式內訊息使用推播訊息的相關資訊。
seo-description: '本節提供如何在Campaign standard中搭配應用程式內訊息使用「Campaign Standard中的推播訊息」的資訊。 '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# 使用位置服務的應用程式內訊息 {#in-app-messages-loc-service}

這些資訊可協助您瞭解如何使用Adobe Experience Platform Location Service資訊來傳送應用程式內訊息或本機通知。

>[!IMPORTANT]
>
>開始之前，請完成下列工作：
>
>* 使用Adobe Experience Platform Mobile SDK設定行動應用程式，包括 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。
   >
   >
* 將 [Adobe Experience Platform Mobile SDK整合至您的應用程式](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
>* 將 [Adobe Campaign Standard Extension新增至您的行動應用程式設定](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。
   >
   >
* [在「地標](/help/poi-mgmt-ui/create-a-poi-ui.md) 」 POI管理介面中建立POI。
   >
   >
* 在您的行動應用 [程式中安裝](/help/places-ext-aep-sdks/places-extension/places-extension.md)[並設定Places擴充功能和Places Monitor擴充功能](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) 。


## 根據地理圍欄進入或退出傳送應用程式內訊息

1. 在您的Adobe Campaign standard例項中，按一下 **[!UICONTROL Create In-App message]**。
2. 對於消息類型，請選擇 **[!UICONTROL Target all users of a Mobile application]**。
3. 按一 **[!UICONTROL Next]** 下並輸入一般詳細資訊。
4. 在左窗格中，確認您現在可以使用與位置服務相關的各種觸發器。

   * 如果使用者已輸入POI地理圍欄，您可以選擇讓應用程式內訊息顯示。
   * 您也可以使用在位置服務UI中定義的中繼資料來篩選對象。
   在下圖中的範例中，您可以觸發應用程式內訊息，該訊息只會顯示給進入其中一個度假勝地且參與免費飲品計畫的使用者，您想要在使用者到達時傳送抵用券。

   ![「應用程式內訊息置入中繼資料」](/help/assets/last-entered-vacation.png)

5. 按一下 **[!UICONTROL Next]** 以完成建立要傳送的應用程式內訊息。

   !["建立事件"](/help/assets/prepare-ACS.png)

   若要測試應用程式內訊息傳送，請在Xcode或Android studio中啟動應用程式，並使用位置模擬器來選取符合訊息標準的POI。

   ![「喝彩券」](/help/assets/drink-coupon-on-app.png)


搭配使用位置服務與Adobe Campaign Standard為您提供強大的工具，讓您根據地理圍欄登入和退出點，將訊息分段並定位給使用者。 此簡單的整合為建立更個人化和情境化的使用案例開啟了大門。

## 在Campaign Standard中根據Places中繼資料建立不同的觸發器

（此資訊是否會傳送）