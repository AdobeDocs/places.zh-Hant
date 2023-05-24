---
title: 應用程式內通知
description: 本節說明如何搭配應用程式內傳訊功能使用Places服務。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 3%

---

# 應用程式內通知 {#places-push-messaging}

下列資訊顯示如何設定從Places Service事件觸發的應用程式內訊息。

>[!IMPORTANT]
>
>訊息必須位於Analytics點選上。

## 應用程式內訊息

Mobile Services可讓您使用傳送至Analytics的位置資料，作為應用程式內訊息的觸發事件及/或條件。 如果從SDK引發應用程式內訊息，而不需要等候Analytics處理資料，只要觸發發生，訊息就會即時出現。

### 本機通知

以下是可用的應用程式內傳訊型別清單：

* 全螢幕
* 警報
* 本機通知

這些型別是應用程式內訊息，因為它們是由SDK觸發。 本機通知的外觀和感覺與推播通知相似，因為前者會在應用程式於背景時顯示。 這些通知也會在應用程式於背景執行時，當使用者進入或離開您的POI時，傳送即時通知。

### 先決條件

開始之前，您會瞭解如何在Mobile Services中傳送和建立應用程式內訊息，以及觸發器如何運作。 如需詳細資訊，請參閱 [建立應用程式內訊息。](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch 中的規則

您可以建立Experience Platform Launch規則，將您想要當作應用程式內訊息觸發器規則的一部分使用的資料傳送至Analytics。 您可以根據使用案例，將Places擴充功能中的資料當做事件和/或條件使用Experience Platform Launch規則。

* 使用位置資料作為觸發事件。

   例如，您可以在使用者輸入POI時，將資料傳送至Analytics。

* 使用位置資料作為觸發事件的條件。

   例如，如果您在Places服務中針對不同POI的天氣建立了自訂中繼資料標籤，您可以將該中繼資料當做規則條件的引數。 雖然您可以將此條件與先前說明的POI專案事件搭配使用，但您也可以使用條件作為任何事件的內容。

使用適當的事件和條件引數設定規則後，請設定動作以將資料傳送至Analytics，以完成規則設定。

## 建立動作

若要建立動作：

1. 選取 **[!UICONTROL Adobe Analytics]** 副檔名。
1. 在 **[!UICONTROL 動作型別]** 下拉式清單，選取 **[!UICONTROL 曲目。]**
1. 輸入動作的名稱。
1. 在右窗格中，在 **[!UICONTROL 內容資料]**，選取索引鍵/值組以設定將傳送至Analytics的內容資料。

例如，您可以選取 `poiname` 作為索引鍵和 `{%%Last Entered POI Name}` 做為值。

>[!TIP]
>
>Analytics處理規則可設定為擷取此內容資料。 如需詳細資訊，請參閱[處理規則](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)。在以下範例中： *建立動作*，動作會傳送 `poiname` 作為內容，說明傳送至Analytics的POI專案事件。

![建立動作](/help/assets/configure-action.png)

以下是完整規則的範例：

![已完成規則](/help/assets/create-a-rule.png)

## 在Mobile Services建立應用程式內訊息

在「觸發器」引數中，您可以透過下列其中一種方式，使用Places服務的資料來建立訊息的對象：

* 使用特定位置的動作，例如登入或退出。
* 使用以內容資料形式傳送的POI中繼資料，以縮小對象目標。

   此選項可與位置特定的動作（例如登入）搭配使用，或作為另一個事件（例如啟動或按鈕點選）的前後關聯。

   以下是如何設定應用程式內訊息的範例，以歡迎使用者進入具有下列專案的POI： **[!UICONTROL Adobe]** 在名稱中：

   ![觸發器引數](/help/assets/trigger-parameters.png)

* 中的Places服務標題中的引數 *觸發器和特徵* Mobile Services中的頁面無法處理Places服務的資料。

   這些引數僅適用於在Mobile Services中建立的舊版Places Service資料庫。
