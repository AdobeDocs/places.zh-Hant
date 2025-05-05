---
title: 定義資料元素
description: 本節提供如何在Experience Platform Launch中為Places建立、使用和發佈資料元素的相關資訊。
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# 定義資料元素 {#define-data-elements}

下列資訊可協助您瞭解資料元素，以及如何建立和發佈它們。

## 關於資料元素

資料元素是應用程式資料字典的建置組塊，用於跨行銷和廣告技術收集、組織和傳遞資料。

資料元素是變數，其值可以對應至訪客ID、電信業者名稱、Advertising ID、推播ID等。 在Experience Platform Launch中，您可以利用變數名稱來參照此值。 此資料元素集合會成為定義資料的字典，您可用來建立規則（事件、條件和動作），而且此字典會在所有Experience Platform Launch間共用，可搭配屬性中的任何擴充功能使用。

使用Places擴充功能，您可以參考以下目標的值：

* 目前POI，代表您的客戶目前所在的POI。

  如果使用者位在多個POI中，則會挑選屬於較高排名之資料庫的POI。 若有多個POI屬於最高排名資料庫，則會挑選半徑最小的POI。
* 上次退出的POI，代表使用者已退出的最新POI。
* 上次輸入的POI，代表使用者最近輸入的POI。

每個POI都包含以下資料參考：

* **[!UICONTROL 類別]**： POI的類別
* **[!UICONTROL 城市]**： POI的城市
* **[!UICONTROL 國家/地區]**： POI的國家/地區
* **[!UICONTROL 緯度]**： POI的緯度
* **[!UICONTROL 經度]**： POI的經度
* **[!UICONTROL 中繼資料]**： POI的自訂中繼資料
* **[!UICONTROL 名稱]**： POI的名稱
* **[!UICONTROL 半徑]**： POI的半徑
* **[!UICONTROL 地區識別碼]**： POI的識別碼
* **[!UICONTROL 地區/州]**： POI的地區、省或州

### 建立資料元素

1. 在應用程式的「屬性」頁面中，按一下「**[!UICONTROL 資料元素]**」標籤。

1. 按一下&#x200B;**[!UICONTROL 「建立新資料元素」]**。

1. 在安裝擴充功能清單中，尋找&#x200B;**[!UICONTROL 地點]**。

1. 在&#x200B;**[!UICONTROL 資料元素型別]**&#x200B;下拉式清單中，選取此資料元素的資料參考。

1. 選取POI目標。

1. 如果此資料元素是自訂中繼資料參考，請選取中繼資料索引鍵。

1. 輸入資料元素的名稱，然後按一下&#x200B;**[!UICONTROL 儲存]**。

   ![建立資料元素](/help/assets/create-de-7-v3.png)


## 使用資料元素

建立資料元素後，如果有資料元素選擇器，您可以使用任何規則元件中的資料元素。

![使用資料元素](/help/assets/use-de-v2.png)

如果規則元件中不存在資料元素選擇器，您可以使用資料元素，方法是以&#x200B;**[!UICONTROL %%]**&#x200B;代號包住資料元素名稱。
例如，如果資料元素名稱為&#x200B;**[!UICONTROL 最後一個POI城市]**，您可以將&#x200B;**[!UICONTROL 最後一個POI城市]**&#x200B;新增至文字輸入。


## Publish資料元素

如果資料元素用於任何規則元件中，這些資料元素也必須包含在程式庫中並發佈。
