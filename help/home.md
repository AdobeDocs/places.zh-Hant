---
title: Places Service
description: Places Service是了解行動使用者參與度的重要內容。 使用此內容，行動應用程式開發人員就能增強應用程式設計，提供更個人化且吸引人的體驗。
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 10%

---

# Places Service {#home}

位置是了解並與行動使用者互動的重要內容。 使用此內容，行動應用程式開發人員就能增強應用程式設計，提供更個人化且吸引人的體驗。

Places Service(舊稱Adobe Experience Platform Location Service)是一項地理位置服務，可讓具備位置感知功能的行動應用程式使用豐富且簡單易用的SDK介面，搭配有彈性的興趣點資料庫(POI)來了解位置環境。

Places Service可讓您達成下列目標：

* 建立並管理可與其他Adobe Experience Cloud解決方案搭配運用的POI資料庫。
* 將自訂中繼資料附加至POI，透過指定其他屬性讓POI更豐富、更有意義。
* 將地圖上的POI視覺化，以便輕鬆了解空間內容，並新增/編輯中繼資料屬性。
* 在Adobe Experience Platform Launch中設定SDK，以定義您的位置觸發規則和中繼資料基礎條件。
* 減少監控裝置位置所需寫入的程式碼，並使用Places擴充功能自動觸發位置特定規則。

這可讓您即時、在何時、何處從位置訊號採取動作。 正確的內容可提供更豐富的行動參與體驗。

以下是一些使用Places的方式：

* 當有人進入POI時傳送即時通知， *「嘿……歡迎來到體育場。」*
* 分析您自己商店與競爭者商店的足流量。
* 使用受眾設定檔搭配位置內容，根據離線行為劃分受眾。
* 在相關時，使用店內體驗來定位使用者。

## Places Service元件

Places Service包含下列元件：

* **網站服務**

   您可以使用Places REST API來建立和管理POI。 如需REST API的詳細資訊，請參閱 [管理程式庫](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) 和 [管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI管理介面**

   在地圖上視覺化POI，以了解空間內容，以及新增/編輯POI及其自訂中繼資料。

* **Places 擴充功能**

   多平台行動API介面，可整合您行動應用程式中的位置內容。 如需SDK的詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **啟動規則**

   地理智慧型Launch規則，可讓您觸發包含登入和退出事件的動作。 規則也可讓您在條件中使用地理屬性，以個人化體驗。

## 術語

以下是本檔案中使用的一些常見辭彙：

* A **興趣點(POI)** 是貴組織感興趣的地理位置。

   您可以使用名稱、半徑、位址、類別和中繼資料標籤等屬性來定義POI。

* A **地理** 是POI的類型。

   此POI類型是由經緯度座標定義的虛擬地理邊界。

* A **信標** 是POI的類型。

   此POI類型是物理裝置，可透過發出低功耗藍芽訊號來代表位置。 信標支援即將推出。

* **資料庫**&#x200B;是 POI 的集合，這些 POI 會分組，以供輕鬆地將規則附加至規則集，而非一個 POI。

* 安 **擴充功能** 是將Places SDK整合至行動應用程式所需的Experience Platform Launch擴充功能。

   與其他行動SDK搭配使用的擴充功能，可將位置內容新增至您的體驗。

* **組織**&#x200B;是 Adobe 實體，可在 Adobe Experience Cloud 中識別您的公司。

   通常，組織就是您的公司名稱。 但是，公司可以有多個組織。 組織管理員可設定群組和使用者，以及設定單一登入功能。

* **orgID** 是在整個 Adobe Experience 平台之中代表您組織的 ID。

   如需詳細資訊，請參閱 [尋找您的orgID](https://forums.adobe.com/thread/2339895).

* 此 **Experience CloudID** 服務提供永續性的通用ID，可識別Experience Cloud中所有解決方案的訪客。

   如需詳細資訊，請參閱[概覽](https://docs.adobe.com/content/help/zh-Hant/id-service/using/intro/overview.html)。
