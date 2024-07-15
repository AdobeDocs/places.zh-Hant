---
title: 應用程式內通知
description: 本節說明如何使用Places服務及應用程式內傳訊。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# 應用程式內通知 {#places-push-messaging}

下列資訊顯示如何設定從Places Service事件觸發的應用程式內訊息。

>[!IMPORTANT]
>
>訊息必須位於Analytics點選上。

## 應用程式內訊息

Mobile Services可讓您使用傳送至Analytics的位置資料，作為應用程式內訊息的觸發事件及/或條件。 如果從SDK引發應用程式內訊息，而且不需要等候Analytics處理資料，一旦觸發就會即時顯示訊息。

### 本機通知

以下是可用的應用程式內訊息型別清單：

* 全螢幕
* 警報
* 本機通知

這些是應用程式內訊息，因為它們是由SDK觸發。 本機通知看起來與推播通知很像，因為當應用程式在背景時就會顯示。 這些通知也會在應用程式於背景執行時，當使用者進入或離開您的POI時，傳送即時通知。

### 先決條件

開始之前，您已瞭解如何在Mobile Services中傳送及建立應用程式內訊息，以及觸發器如何運作。 如需詳細資訊，請參閱[建立應用程式內訊息。](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=zh-Hant)

## Experience Platform Launch中的規則

您可以建立Experience Platform Launch規則，將您想要用作為應用程式內訊息觸發器規則一部分的資料傳送至Analytics。 您可以視使用案例而定，將Places擴充功能中的資料用作Experience Platform Launch規則中的事件和/或條件。

* 使用位置資料作為觸發事件。

  例如，您可以在使用者輸入POI時，將資料傳送至Analytics。

* 使用位置資料作為觸發事件的條件。

  例如，如果您在Places服務中針對不同POI的天氣建立了自訂中繼資料標籤，您可以將該中繼資料當作規則條件的引數。 雖然您可以將此條件與先前所述的POI專案事件搭配使用，但您也可以使用條件作為任何事件的內容。

使用適當的事件和條件引數設定規則後，請設定將資料傳送至Analytics的動作，以完成規則設定。

## 建立動作

若要建立動作：

1. 選取&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;擴充功能。
1. 在&#x200B;**[!UICONTROL 動作型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 追蹤。]**
1. 輸入動作的名稱。
1. 在右窗格的&#x200B;**[!UICONTROL 內容資料]**&#x200B;中，選取索引鍵/值組以設定將傳送至Analytics的內容資料。

例如，您可以選取`poiname`作為索引鍵，並選取`{%%Last Entered POI Name}`作為值。

>[!TIP]
>
>Analytics處理規則可以設定為擷取此內容資料。 如需詳細資訊，請參閱[處理規則](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html)。 在&#x200B;*建立動作*&#x200B;的範例中，動作會傳送`poiname`作為內容，以說明傳送至Analytics的POI專案事件。

![建立動作](/help/assets/configure-action.png)

以下是完整規則的範例：

![已完成規則](/help/assets/create-a-rule.png)

## 在行動服務中建立應用程式內訊息

在「觸發器」引數中，您可以透過下列其中一種方式，使用Places服務的資料建立訊息的對象：

* 使用特定位置的動作，例如登入或退出。
* 使用以內容資料形式傳送的POI中繼資料，以縮小對象目標。

  此選項可與位置特定的動作（例如登入）搭配使用，或作為另一個事件（例如啟動或按鈕點選）的前後關聯。

  以下是如何設定應用程式內訊息的範例，以歡迎使用者輸入名稱中有&#x200B;**[!UICONTROL Adobe]**&#x200B;的POI：

  ![觸發引數](/help/assets/trigger-parameters.png)

* Mobile Services中&#x200B;*觸發器和特徵*&#x200B;頁面的Places服務標題中的引數，無法與Places服務的資料搭配使用。

  這些引數僅適用於在Mobile Services中建立的舊版Places Service資料庫。
