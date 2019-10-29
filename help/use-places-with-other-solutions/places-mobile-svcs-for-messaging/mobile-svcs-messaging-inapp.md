---
title: 應用程式內訊息
seo-title: 應用程式內訊息
description: 本節將說明如何搭配應用程式內訊息使用「地標」。
seo-description: 本節將說明如何搭配應用程式內訊息使用「地標」。
translation-type: tm+mt
source-git-commit: 7985943cef606525401983c4c80862c277f41bf0

---


# 應用程式內通知(#places-push-messaging)

如何設定應用程式內訊息以從「地標」事件觸發；訊息必須位於Analytics點擊上。

## 應用程式內訊息

AMS可讓您使用傳送至Analytics的位置資料作為應用程式內訊息的觸發事件和／或條件。 從SDK引發觸發器時，應用程式內訊息可立即顯示給使用者，而不需等待Analytics處理資料。

本機通知：應用程式內訊息有3種不同類型：

* 全螢幕
* 警報
* 本機通知。

這些類型符合應用程式內訊息的資格，因為這些訊息是由SDK觸發，但請務必注意，當本機通知在應用程式未在前景時，其外觀和感覺就像推播通知。 當使用者在應用程式背景時進入或退出您的POI時，本機通知是提供即時通知的絕佳選項。 請參閱Places Monitor擴充功能檔案以瞭解位置監視(https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension)。

### 先決條件

* 瞭解如何在AMS中傳送和建立應用程式內訊息，以及觸發程式的運作方式。

   如需詳細資訊，請參閱[建立應用程式內訊息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)。


## 在Experience Platform Launch中建立規則

建立啟動規則，將正確的資料傳送至Analytics，以便能夠用作應用程式內訊息觸發規則的一部分。 您可以根據使用案例，將Launch規則中Places擴充功能的資料當做事件和／或條件使用。

* 使用位置資料作為觸發事件。 例如，如果您想在使用者輸入POI時傳送資料至Analytics。

* 使用位置資料作為觸發事件的條件。 例如，如果您在位置服務中針對不同POI的天氣建立自訂中繼資料標籤，則可將該中繼資料用作規則條件的參數，如下所示。 雖然您可以將此條件用於前面所述的POI參加項目事件，但您也可以將它用作任何事件的上下文。

設定規則時，請設定動作以傳送資料至Analytics，以完成規則設定。 要執行此操作：

* 選擇Adobe Analytics做為擴充功能
* 選擇「追蹤」作為動作類型
* 確定動作的名稱
* 設定要隨事件一起傳送的上下文資料。 使用「內容資料」介面，將「啟動資料元素」對應至您要傳送至Analytics的關鍵名稱。

請注意，可以設定「Analytics處理規則」來擷取此上下文資料。 如有需要，請參閱Analytics處理規則(https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)例如，此動作會以內容形式在點名中傳送，以說明要傳送至Analytics的POIentry事件。

![建立操作](/help/assets/configure-action.png)

以下是完成規則的範例。

![已完成規則](/help/assets/create-a-rule.png)

## 在AMS中建立應用程式內訊息：

您會使用來自位置服務的資料來建立訊息的對象，做為觸發器參數的一部分。

* 使用特定位置的動作，例如進入或退出
* 使用以內容資料形式傳送的POI中繼資料，以縮小對象的目標。 這可與特定位置的動作（例如登入）搭配使用，或可當成其他事件（例如啟動或按鈕點按）的上下文。

   以下範例說明如何設定應用程式內訊息以歡迎輸入名稱中包含"Adobe"的POI的使用者：

   ![觸發參數](/help/assets/trigger-parameters.png)

* 在AMS觸發器和特徵中的「位置」標題中找到的參數無法與位置服務的資料一起使用。 這些參數用於在AMS中建立的舊版Places資料庫。