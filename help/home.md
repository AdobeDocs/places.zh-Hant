---
title: Places Service
description: Places Service是瞭解行動使用者參與的重要內容。 透過使用此內容，行動應用程式開發人員可以增強應用程式設計，使其成為更個人化且吸引人的體驗。
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Places Service {#home}

位置是瞭解及與行動使用者互動的重要內容。 透過使用此內容，行動應用程式開發人員可以增強應用程式設計，使其成為更個人化且吸引人的體驗。

Places Service (先前稱為Adobe Experience Platform Location Service)是一項地理位置服務，可讓具備位置感知功能的行動應用程式使用豐富且簡單易用的SDK介面，搭配有彈性的興趣點資料庫(POI)來瞭解位置環境。

Places Service可讓您達成下列目標：

* 建立並管理可與其他Adobe Experience Cloud解決方案搭配使用的POI資料庫。
* 將自訂中繼資料附加至POI，可指定其他屬性，讓這些POI更豐富且更有意義。
* 將地圖上的POI視覺化以輕鬆瞭解空間內容並新增/編輯中繼資料屬性。
* 在Adobe Experience Platform Launch中設定SDK，以定義您的位置觸發式規則和中繼資料型條件。
* 減少您需要撰寫以監視裝置位置的程式碼，並使用Places擴充功能自動觸發位置特定規則。

這可讓您在需要的時間和地點即時從位置訊號執行動作。 正確的內容可提供更豐富的行動參與體驗。

以下是您使用「地點」的一些方式：

* 當有人進入POI時傳送即時通知， *「嗨……歡迎來到體育場。」*
* 分析您自己的商店與競爭對手商店的客流量。
* 使用具有位置內容的對象設定檔，根據離線行為來細分對象。
* 在相關時鎖定具有店內體驗的使用者。

## Places服務元件

Places Service包含下列元件：

* **Web服務**

  您可以使用Places REST API來建立和管理POI。 如需REST API的詳細資訊，請參閱 [管理程式庫](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) 和 [管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **poi管理介面**

  在地圖上視覺化POI，以瞭解空間內容並新增/編輯POI及其自訂中繼資料。

* **Places擴充功能**

  多平台行動API介面，用於將位置內容整合到行動應用程式中。 如需SDK的詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Launch規則**

  地理智慧的Launch規則，可讓您透過登入和退出事件觸發動作。 規則也可讓您在條件中使用地理屬性，以個人化體驗。

## 術語

以下是本檔案中所使用的一些常用辭彙：

* A **興趣點(POI)** 是貴組織感興趣的地理位置。

  您可以使用名稱、半徑、地址、類別和中繼資料標籤等屬性來定義POI。

* A **地理圍欄** 是POI型別。

  此POI型別是由經緯度座標定義的虛擬地理邊界。

* A **beacon** 是POI型別。

  此POI型別是一種實體裝置，可透過發出低功率藍芽訊號來代表位置。 未來版本將提供Beacons支援。

* **資料庫**&#x200B;是 POI 的集合，這些 POI 會分組，以供輕鬆地將規則附加至規則集，而非一個 POI。

* 一個 **副檔名** 是在行動應用程式中整合Places SDK所需的Experience Platform Launch擴充功能。

  搭配其他行動SDK使用的擴充功能，可將位置內容新增至您的體驗。

* **組織**&#x200B;是 Adobe 實體，可在 Adobe Experience Cloud 中識別您的公司。

  通常，組織就是您的公司名稱。 但是，公司可以有多個組織。 組織管理員可以設定群組和使用者，以及設定單一登入功能。

* **orgID** 是在整個 Adobe Experience 平台之中代表您組織的 ID。

  如需詳細資訊，請參閱 [尋找您的orgID](https://forums.adobe.com/thread/2339895).

* 此 **EXPERIENCE CLOUDID** 服務提供永續性的通用ID，可識別Experience Cloud中所有解決方案的訪客。

  如需詳細資訊，請參閱[概覽](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=zh-Hant)。

