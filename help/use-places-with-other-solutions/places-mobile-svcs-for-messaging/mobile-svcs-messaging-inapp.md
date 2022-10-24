---
title: 應用程式內通知
description: 本節說明如何將Places Service與應用程式內傳訊搭配使用。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 3%

---

# 應用程式內通知 {#places-push-messaging}

下列資訊會示範如何設定應用程式內訊息，以從Places Service事件觸發。

>[!IMPORTANT]
>
>訊息必須位於Analytics點擊上。

## 應用程式內訊息

Mobile Services可讓您使用傳送至Analytics的位置資料，做為應用程式內訊息的觸發事件和/或條件。 如果從SDK觸發應用程式內訊息，且不需要等待Analytics處理資料，則觸發時訊息可立即顯示。

### 本機通知

以下是可用的應用程式內訊息類型清單：

* 全螢幕
* 警報
* 本機通知

這些類型是應用程式內訊息，因為是由SDK觸發。 本機通知的外觀和感覺就像推播通知，因為這些通知會在應用程式於背景時顯示。 當使用者在應用程式於背景時進入或退出您的POI時，這些通知也會傳送即時通知。

### 先決條件

開始之前，您已了解如何在Mobile Services中傳送和建立應用程式內訊息，以及觸發程式的運作方式。 如需詳細資訊，請參閱 [建立應用程式內訊息。](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch 中的規則

您可以建立Experience Platform Launch規則，將您想要用於應用程式內訊息觸發規則的資料傳送至Analytics。 您可以根據您的使用案例，將來自Places擴充功能的資料用作Experience Platform Launch規則中的事件和/或條件。

* 使用位置資料作為觸發事件。

   例如，您可以在使用者輸入POI時將資料傳送至Analytics。

* 使用位置資料作為觸發事件的條件。

   例如，如果您在Places Service中針對不同POI的天氣建立自訂中繼資料標籤，可以將該中繼資料當作規則條件的參數。 雖然您可以將此條件與先前所述的POI項目事件搭配使用，但您也可以將條件當作任何事件的內容使用。

使用正確的事件和條件參數設定規則後，請設定要將資料傳送至Analytics的動作，以完成規則設定。

## 建立動作

若要建立動作：

1. 選取 **[!UICONTROL Adobe Analytics]** 擴充功能。
1. 在 **[!UICONTROL 動作類型]** 下拉清單，選擇 **[!UICONTROL 追蹤。]**
1. 輸入動作的名稱。
1. 在右窗格中， **[!UICONTROL 內容資料]**，選取機碼值組，以設定要傳送至Analytics的內容資料。

例如，您可以選取 `poiname` 作為鍵和 `{%%Last Entered POI Name}` 作為值。

>[!TIP]
>
>可設定Analytics處理規則來擷取此內容資料。 如需詳細資訊，請參閱[處理規則](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)。在 *建立動作*，動作會傳送 `poiname` 說明傳送至Analytics之POI項目事件的內容。

![建立動作](/help/assets/configure-action.png)

以下是完整規則的範例：

![已完成規則](/help/assets/create-a-rule.png)

## 在Mobile Services中建立應用程式內訊息

在觸發程式參數中，您可以透過下列其中一種方式，使用Places Service的資料建立訊息的對象：

* 使用特定位置的動作，例如登入或退出。
* 使用以內容資料傳送的POI中繼資料，以縮小對象的目標範圍。

   此選項可搭配位置特定動作（例如登入）使用，或可作為其他事件（例如啟動或按鈕點按）的內容。

   以下範例說明如何設定應用程式內訊息，以歡迎進入具有 **[!UICONTROL Adobe]** 名稱中：

   ![觸發參數](/help/assets/trigger-parameters.png)

* Places服務標題中的參數 *觸發器和特徵* 頁面無法搭配Places服務的資料使用。

   這些參數僅適用於在Mobile Services中建立的舊版Places Service資料庫。
