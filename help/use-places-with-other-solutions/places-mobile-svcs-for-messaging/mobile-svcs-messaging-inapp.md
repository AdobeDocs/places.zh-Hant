---
title: 應用程式內通知
description: 本節將說明如何搭配應用程式內訊息使用「地標」。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# 應用程式內通知(#places-push-messaging)

下列資訊將說明如何設定「應用程式內訊息」，以便從「位置」事件觸發。

>[!IMPORTANT]
>
>訊息必須位於Analytics點擊上。

## 應用程式內訊息

Mobile services可讓您使用傳送至Analytics的位置資料作為應用程式內訊息的觸發事件和／或條件。 如果從SDK引發應用程式內訊息，而不需要等待Analytics處理資料，則觸發器一發生，訊息就會即時顯示。

### 本機通知

以下是可用的應用程式內訊息類型清單：

* 全螢幕
* 警報
* 本機通知

這些類型是應用程式內訊息，因為是由SDK觸發。 本機通知的外觀和感覺就像推播通知，因為當應用程式在背景時，這些通知就會出現。 當使用者在應用程式背景時進入或退出您的POI時，這些通知也會傳送即時通知。 如需詳細資訊，請參 [閱「置入螢幕擴充功能](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)」。

### 必要條件

在開始之前，您會先瞭解如何在Mobile services中傳送和建立應用程式內訊息，以及觸發程式的運作方式。 For more information, see [Create an in-app message.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch 中的規則

您可以建立「啟動」規則，將您想要能用作應用程式內訊息「觸發規則」一部分的資料傳送至Analytics。 您可以根據使用案例，將Launch規則中Places擴充功能的資料當做事件和／或條件使用。

* 使用位置資料作為觸發事件。

   例如，當使用者輸入POI時，您可以傳送資料至Analytics。

* 使用位置資料作為觸發事件的條件。

   例如，如果您在位置服務中針對不同POI的天氣建立自訂中繼資料標籤，則可將該中繼資料用作規則條件的參數。 雖然您可以將此條件與前面所述的POI參加項目事件搭配使用，但您也可以將該條件用作任何事件的上下文。

設定規則時，請設定動作，將資料傳送至Analytics，以完成規則設定。

## 建立動作

要建立操作，請執行以下操作：

1. 選取 **[!UICONTROL Adobe Analytics]**擴充功能。
1. 在下拉 **[!UICONTROL Action type]**式清單中，選取**[!UICONTROL Track.]**
1. 鍵入動作的名稱。
1. 在右窗格中，選 **[!UICONTROL Context Data]**取鍵值對，以設定將傳送至Analytics的內容資料。

例如，您可以選 `poiname` 擇作為鍵 `{%%Last Entered POI Name}` 和值。

>[!TIP]
>
>可以設定「分析處理規則」來擷取此上下文資料。 如需詳細資訊，請參閱[處理規則](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)。在「建立 *動作*」中的範例中，「動作」會傳送作 `poiname` 為內容，以說明要傳送至Analytics的POI項目事件。

![建立操作](/help/assets/configure-action.png)

以下是完整規則的範例：

![已完成規則](/help/assets/create-a-rule.png)

## 在Mobile services中建立應用程式內訊息

在觸發器參數中，您可以透過下列其中一種方式，使用位置服務的資料來建立訊息的對象：

* 使用特定位置的動作，例如登入或退出。
* 使用以內容資料傳送的POI中繼資料，以縮小對象的目標。

   此選項可與特定位置的動作（例如登入）搭配使用，或可當成啟動或按鈕點選等其他事件的上下文。

   以下範例說明如何設定應用程式內訊息以歡迎輸入名稱中包含POI **[!UICONTROL Adobe]**的使用者：

   ![觸發參數](/help/assets/trigger-parameters.png)

* Mobile services中「觸發器」和「特 *徵」頁面中* ,「置入」標題的參數無法與「位置服務」中的資料搭配使用。

   這些參數僅適用於在Mobile services中建立的舊版Places資料庫。