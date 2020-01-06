---
title: 定義資料元素
description: 本節提供如何在Experience Platform Launch for Places中建立、使用和發佈資料元素的相關資訊。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Define a data element {#define-data-elements}

下列資訊可協助您瞭解資料元素，以及如何建立和發佈資料元素。

## 關於資料元素

資料元素是應用程式資料字典的建置區塊，用來收集、組織和傳送跨行銷和廣告技術的資料。

資料元素是一個變數，其中值可映射至訪客ID、電信業者名稱、廣告ID、推播ID等。 在Experience Platform Launch中，您可以透過其變數名稱來參考此值。 此資料元素的集合會變成定義資料的字典，您可用來建立規則（事件、條件和動作），此字典會跨Experience Platform Launch共用，可與屬性中的任何擴充功能搭配使用。

使用「位置」(Places)副檔名，您可以從下列目標引用值：

* 目前的POI，指您的客戶目前所在的POI。

   如果使用者位於多個POI中，則會選取該POI屬於排名較高的程式庫。 如果多個POI屬於最高秩庫，則會選擇半徑最小的POI。
* 上次退出POI，是指使用者退出的最近POI。
* 上次輸入的POI，是指使用者輸入的最新POI。

每個POI都包含下列資料參考：

* **[!UICONTROL Category]**:POI的類別
* **[!UICONTROL City]**:POI城市
* **[!UICONTROL Country]**:POI的國家／地區
* **[!UICONTROL Latitude]**:POI的緯度
* **[!UICONTROL Longitude]**:POI的經度
* **[!UICONTROL Metadata]**:POI的自訂中繼資料
* **[!UICONTROL Name]**:POI地區
* **[!UICONTROL Radius]**:POI半徑
* **[!UICONTROL Region ID]**:POI的ID
* **[!UICONTROL Region/State]**:POI的地區、省或州

### 建立資料元素

1. 在應用程式的「屬性」頁面中，按一下標 **[!UICONTROL Data Elements]**簽。

1. 按一下 **[!UICONTROL Create New Data Element]**。

1. 在已安裝的擴充功能清單中，尋找 **[!UICONTROL Places]**。

1. 在下拉 **[!UICONTROL Data Element Type]**式清單中，選取此資料元素的資料參考。

1. 選擇POI目標。

1. 如果此資料元素是自訂中繼資料參考，請選取中繼資料索引鍵。

1. 輸入資料元素的名稱，然後按一下 **[!UICONTROL Save]**。

   ![建立資料元素](/help/assets/create-de-7-v3.png)


## 使用資料元素

建立資料元素後，如果有資料元素選擇器，您可以使用任何規則元件的資料元素。

![使用資料元素](/help/assets/use-de-v2.png)

如果規則元件中沒有資料元素選擇器，您可以使用Token來封裝資料元素名稱，以使用資料 **[!UICONTROL %%]**元素。
例如，如果資料元素名稱為**[!UICONTROL Last POI City]**，您可以新增 **[!UICONTROL LAST POI City]**至文字輸入。


## 發佈資料元素

如果任何規則元件都使用資料元素，這些資料元素也必須包含在程式庫中並發佈。
