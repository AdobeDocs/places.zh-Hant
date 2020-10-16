---
title: Places服務的應用程式內訊息
description: 本節提供如何在Campaign Standard中搭配Campaign Standard中的應用程式內訊息使用推播訊息的相關資訊。
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---


# 使用Places服務的應用程式內訊息 {#in-app-messages-loc-service}

這些資訊可協助您瞭解如何使用Places服務資訊來傳送應用程式內訊息或本機通知。

## 必要條件

開始之前，請完成下列工作：

* 使用Adobe Experience Platform Mobile SDK設定行動應用程式，包括 [Adobe Campaign Standard擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 將 [Adobe Experience Platform Mobile SDK整合至您的應用程式](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
* 將 [Adobe Campaign Standard Extension新增至您的行動應用程式設定](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。

* [在Places Service](/help/poi-mgmt-ui/create-a-poi-ui.md) POI管理介面中建立POI。

* 在您的行動應用 [程式中安裝](/help/places-ext-aep-sdks/places-extension/places-extension.md)[並設定Places擴充功能和Places Monitor擴充功能](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) 。

## 根據地理圍欄進入或退出傳送應用程式內訊息

1. 在您的Adobe Campaign Standard例項中，按一下 **[!UICONTROL Create In-App message]**。
1. 對於消息類型，選擇 **[!UICONTROL Target all users of a Mobile application]**。
1. 按一 **[!UICONTROL Next]** 下並輸入一般詳細資訊。
1. 在左窗格中，確認您可以使用與「地標服務」相關的各種觸發器。

   * 如果使用者已輸入POI地理圍欄，您可以選擇讓應用程式內訊息顯示。
   * 您也可以使用在「地標服務」使用者介面中定義的中繼資料來篩選對象。

   在下列範例中，您可以觸發應用程式內訊息，該訊息只會顯示給進入其中一個度假勝地且參加免費飲品計畫的使用者，而您想要在這些使用者到達時傳送抵用券。

   ![「應用程式內訊息置入中繼資料」](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]** to finish creating the In-app message for delivery.

   ![&quot;建立事件&quot;](/help/assets/prepare-ACS.png)

   若要測試應用程式內訊息傳送，請在Xcode或Android Studio中啟動應用程式，並使用位置模擬器來選取符合訊息標準的POI。

   ![「喝彩券」](/help/assets/drink-coupon-on-app.png)

搭配使用Places Services與Adobe Campaign Standard為您提供強大的工具，讓您根據地理圍欄的登入與退出點，將訊息分段並鎖定給使用者。 此整合可讓您建立更個人化和情境化的使用案例。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform定位服務與宣傳訊息](https://www.youtube.com/watch?v=ikiTTQw9c-o)
