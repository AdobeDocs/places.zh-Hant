---
title: '網站服務API概觀 '
seo-title: '網站服務API概觀 '
description: Places是一套服務，可讓Adobe客戶更輕鬆地在適當的時間和地點，將Adobe Experience cloud和Adobe Experience platform解決方案加入位置資料，並為適當的人提供適當的體驗。
seo-description: Places是一套服務，可讓Adobe客戶更輕鬆地在適當的時間和地點，將Adobe Experience cloud和Adobe Experience platform解決方案加入位置資料，並為適當的人提供適當的體驗。
translation-type: tm+mt
source-git-commit: e899cde6230353c8b34090c793983dc570e8115e

---


# 網站服務API概觀 {#places-web-services-api}

Places是一套服務，可讓Adobe客戶更輕鬆地在適當的時間和地點，將Adobe Cloud platform和Adobe Experience platform解決方案加入位置資料，並為適當的人提供適當的體驗。

web services API可讓您執行下列動作：

* 管理地理柵欄
* 即使應用程式在背景，也能測量使用者的位置
* 在重要時即時使用資料

本節提供如何使用REST API和POI資料庫的資訊，此資料庫包含您組織的POI資料。

## REST API

Places REST API可讓您以程式設計方式處理組織的POI。 這些API可讓您建立、更新和刪除您的資料庫，以及這些資料庫中的POI。 這些API使用JavaScript物件標籤(JSON)標準來格式化傳送和接收的資料。 JSON的主要優點是讓開發人員和機器可輕鬆編寫、讀取和剖析API查詢。

在您使用web services API之前，請確定已符合下列需求：

* 您的組織已布建地點，而且您以使用者身分擁有適當的存取權。

   如需詳細資訊，請參 *閱下方的* 「組織需求」一節。

* 在您的組織中布建「地標」後，而且您擁有存取權，請建立「地標」的Adobe整合。

   如需詳細資訊，請參 *閱「在* Adobe I/O整合概觀中建立Places整合」 [](/help/web-service-api/adobe-i-o-integration.md)。

其他資訊:

* 如需可用API的詳細資訊以及如何使用這些API的詳細資訊，請參 [閱管理程式庫](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)[和管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* 如需這些API中標題和參數的詳細資訊，請參閱標 [題和參數](/help/web-service-api/api-usage/headers-and-parameters.md)。