---
title: Adobe Experience Platform Location Service
description: '位置服務是瞭解行動使用者參與度的重要內容。 運用這個情境，行動應用程式開發人員就可以增強應用程式設計，讓它成為更個人化、更吸引人的體驗。 '
translation-type: tm+mt
source-git-commit: c20e720d23121970bb2fa1c63a2fd1e81c84b977

---


# Adobe Experience Platform位置服務總覽 {#home}

![「Adobe Experience Platform Location Service」](/help/assets/LocationHeader.png)

位置是瞭解行動使用者並與之互動的重要內容。 運用這個情境，行動應用程式開發人員就可以增強應用程式設計，讓它成為更個人化、更吸引人的體驗。

Adobe Experience Platform Location Service(Location Service)是地理位置服務，可讓具備位置感知的行動應用程式使用豐富且簡單易用的SDK介面，加上有彈性的興趣點資料庫(POI)，來瞭解位置環境。

位置服務可讓您達成下列目標：

* 建立並管理可與其他Adobe Experience cloud解決方案搭配運用的POI資料庫。
* 將自訂中繼資料附加至POI，透過指定其他屬性，讓POI更豐富、更有意義。
* 在地圖上視覺化POI，以輕鬆瞭解空間內容並新增／編輯中繼資料屬性。
* 在Adobe Experience Platform Launch中設定SDK，以定義您的位置觸發規則和中繼資料條件。
* 減少監控裝置位置時需要編寫的程式碼，並使用「位置」擴充功能自動觸發特定位置的規則。

這可讓您即時、在何時、何地從位置訊號採取動作。 正確的情境可提供更豐富的行動互動體驗。

以下是您使用「地標」的一些方式：

* 當有人輸入POI時，傳送即時通 *知，&quot;嘿……歡迎來到體育場。」*
* 分析您自有商店與競爭對手商店的足路流量。
* 使用具有位置內容的受眾個人檔案，根據離線行為劃分受眾。
* 在相關時，以店內體驗為目標使用者。

## 位置服務元件

位置服務包含下列元件：

* **Web服務**

   您可以使用Places REST API來建立和管理POI。 如需REST API的詳細資訊，請參 [閱管理程式庫](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)[和管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。

* **POI管理介面**

   在地圖上視覺化POI，以瞭解空間內容，並新增／編輯POI及其自訂中繼資料。

* **Places 擴充功能**

   多平台行動API介面，可整合行動應用程式中的位置內容。 如需SDK的詳細資訊，請參閱「地 [標擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)」。

* **啟動規則**

   地理智慧型啟動規則，可讓您使用登入和退出事件觸發動作。 這些規則也可讓您在條件中使用地理屬性來個人化體驗。

* **Places Monitor擴充功能**

   多平台行動SDK可內嵌在您的行動應用程式中，以自動監控使用者的位置變更並觸發「地標」規則。 如需詳細資訊，請參 [閱Places Monitor擴充功能](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

## 術語

以下是本檔案中使用的一些常見術語：

* 興 **趣點(POI)** ，是您組織感興趣的地理位置。

   您可以定義具有名稱、半徑、地址、類別和中繼資料標籤等屬性的POI。

* 地 **緣** ，是POI的一種類型。

   此POI類型是由經緯度坐標定義的虛擬地理邊界。

* 信 **標是** POI的一種類型。

   該POI類型是通過發射低功率藍芽信號來表示位置的物理設備。 Beacon支援即將推出。

* **資料庫**&#x200B;是 POI 的集合，這些 POI 會分組，以供輕鬆地將規則附加至規則集，而非一個 POI。

* 擴 **充功能** 是Experience Platform Launch擴充功能，您必須將Places SDK整合在行動應用程式中。

   與其他行動SDK一起使用的擴充功能，可將位置內容新增至您的體驗。

* **組織**&#x200B;是 Adobe 實體，可在 Adobe Experience Cloud 中識別您的公司。

   通常，組織是您的公司名稱。 但是，公司可以有多個組織。 組織管理員可以設定群組和使用者，以及設定單一登入功能。

* **orgID** 是在整個 Adobe Experience Platform 之中代表您組織的 ID。

   如需詳細資訊，請參 [閱尋找組織ID](https://forums.adobe.com/thread/2339895)。

* **Experience Cloud ID服務提供通用、永續性的ID** ，可識別Experience cloud中所有解決方案的訪客。

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).
