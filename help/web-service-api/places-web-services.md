---
title: 網站服務API總覽
description: Places Service是一組服務，可讓Adobe客戶更輕鬆地在正確的時間和正確的地點，將Adobe Experience Cloud和Adobe Experience Platform解決方案與位置資料和正確的體驗水合在一起。
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
TQID: https://experienceleague.adobe.com/jP7iQH7X85UZROjsa3XzuN0bJZjjKffODFGGji7XZfQ
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 0%

---

# 網站服務API總覽 {#places-web-services-api}

Places Service是一組服務，可讓Adobe客戶更輕鬆地在正確的時間和正確的地點，將Adobe Cloud Platform和Adobe Experience Platform解決方案與位置資料和正確的體驗水合在一起。

網站服務API可讓您進行以下工作：

* 管理地理圍欄
* 測量使用者位置，即使應用程式在背景亦然
* 在重要時即時使用資料

本節提供如何使用REST API和POI資料庫（其中包含您組織的POI資料）的相關資訊。

## REST API

Places Service REST API可讓您以程式設計方式使用組織的POI。 這些API可讓您建立、更新和刪除程式庫以及這些程式庫中的POI。 這些API使用JavaScript物件標籤法(JSON)標準來格式化所傳送和接收的資料。 JSON的主要優點在於，它可讓API查詢易於開發人員和電腦寫入、讀取和分析。

使用Web服務API之前，請先確定已符合下列要求：

* Places Service已布建在您的組織中，而且您擁有適當的使用者存取權。

  如需詳細資訊，請參閱[整合總覽與必要條件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*使用者存取的必要條件*。

* 在您的組織中布建Places服務，而且您擁有存取權後，請為Places服務建立Adobe整合。

  如需詳細資訊，請參閱[整合總覽和先決條件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*建立Places服務整合*。

其他資訊：

* 如需可用API及其使用方式的詳細資訊，請參閱[管理資料庫](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)和[管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* 如需這些API中標題和引數的詳細資訊，請參閱[標題和引數](/help/web-service-api/api-usage/headers-and-parameters.md)。
