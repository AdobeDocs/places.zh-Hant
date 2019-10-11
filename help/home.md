---
title: Adobe Places概觀
seo-title: Adobe Places概觀
description: 'Adobe Places是瞭解行動使用者參與度的重要內容。 運用這個情境，行動應用程式開發人員就可以增強應用程式設計，讓它成為更個人化、更吸引人的體驗。 '
seo-description: '地點是瞭解行動使用者參與度的重要內容。 運用這個情境，行動應用程式開發人員就可以增強應用程式設計，讓它成為更個人化、更吸引人的體驗。 '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 概述 {#home}

Adobe Places是瞭解行動使用者參與度的重要內容。 運用這個情境，行動應用程式開發人員就可以增強應用程式設計，讓它成為更個人化、更吸引人的體驗。 Places是地理位置服務，可讓行動應用程式開發人員使用豐富且簡單易用的SDK介面，加上有彈性的興趣點資料庫(POI)，來瞭解位置環境。

Places可讓您達成下列目標：

* 建立並管理可與其他Adobe Experience cloud解決方案搭配運用的POI資料庫。
* 將自訂中繼資料附加至POI，透過指定其他屬性，讓POI更豐富、更有意義。
* 在地圖上視覺化POI，以輕鬆瞭解空間內容並新增／編輯中繼資料屬性。
* 在Adobe Experience Platform Launch中設定SDK，以定義您的位置觸發規則和中繼資料條件。
* 減少您需要寫入螢幕裝置位置的程式碼，並使用Adobe的位置監視器自動觸發特定位置的規則。

這可讓您即時、在何時、何地從位置訊號採取動作。 正確的情境可提供更豐富的行動互動體驗。

以下是您使用「地標」的一些方式：

* 當有人輸入POI時，傳送即時通 *知，"嘿……歡迎來到體育場。」*
* 分析您自有商店與競爭對手商店的足路流量。
* 使用具有位置內容的受眾個人檔案，根據離線行為劃分受眾。
* 在相關時，以店內體驗為目標使用者。

## 放置元件

地點包括下列元件：

* **放置Web服務**

   您可以使用REST API來建立和管理POI。 如需REST API的詳細資訊，請參閱「置 [入網站服務」](/help/places-rest-apis/api-usage/api-usage.md)。

* **Places UI**

   在地圖上視覺化POI，以瞭解空間內容，並新增／編輯POI及其自訂中繼資料。

* **位置SDK**

   多平台行動API介面，可整合行動應用程式中的位置內容。 如需SDK的詳細資訊，請參閱「地 [標擴充功能](/help/configure-places-in-the-sdk/places-extension/places-extension.md)」。

* **位置規則**

   地理智慧型啟動規則，可讓您使用登入和退出事件觸發動作。 這些規則也可讓您在條件中使用地理屬性來個人化體驗。

* **Places Monitor**

   多平台行動SDK可內嵌在您的行動應用程式中，以自動監控使用者的位置變更並觸發「地標」規則。 如需詳細資訊，請參 [閱Places Monitor擴充功能](/help/configure-places-in-the-sdk/places-monitor-extension/places-monitor-extension.md)。

## 術語

以下是本檔案中使用的一些常見術語：

* 興 **趣點(POI)** ，是您組織感興趣的地理位置。

   您可以定義具有名稱、半徑、地址、類別和中繼資料標籤等屬性的POI。

* 地 **緣** ，是POI的一種類型。

   此POI類型是由經緯度坐標定義的虛擬地理邊界。

* 信 **標是** POI的一種類型。

   該POI類型是通過發射低功率藍芽信號來表示位置的物理設備。 Beacon支援即將推出。

* 程 **式庫** 是POI的集合，這些POI會分組，以輕鬆將規則附加至規則集，而非一個POI。

* SDK擴 **充功能**，是將Places SDK整合在行動應用程式中所需的Experience Platform Launch擴充功能。

   與其他行動SDK一起使用的擴充功能，可將位置內容新增至您的體驗。

* 組 **織是** Adobe實體，可在Adobe Experience cloud中識別您的公司。

   通常，組織是您的公司名稱。 但是，公司可以有多個組織。 組織管理員可以設定群組和使用者，以及設定單一登入功能。

* 組 **織ID** 是代表整個Adobe Experience platform中組織的ID。

   如需詳細資訊，請參 [閱尋找組織ID](https://forums.adobe.com/thread/2339895)。

* **Experience Cloud ID服務提供通用、永續性的ID** ，可識別Experience cloud中所有解決方案的訪客。

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).

## 瞭解地標UI

若要存取Places UI，請在瀏覽器中前往 [Places UI](https://places.adobe.com) ，並使用您的Adobe ID登入。

以下是一些基本資訊，可協助您熟悉UI:

* 在右上角，您可以按一下按鈕來建立資料庫、POI和篩選搜尋。
* 在畫面的右下角，有一些按鈕可讓您以目前位置為中心來放大和縮小 **[!UICONTROL Find Me]**，以及在地圖檢視和衛星檢視之間切換。
* 按兩下以放大，或按一下並拖曳以重新輸入地圖。
* 您也可以使用方向鍵來捲動地圖。

![](assets/location-services.png)


## Places工作流程

以下是「地標」工作流程的高階檢視：

![](/help/assets/places-workflow-diagram-lc-1.png)