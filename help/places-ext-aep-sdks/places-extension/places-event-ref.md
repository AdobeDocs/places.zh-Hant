---
title: Places事件參考
description: Places擴充功能所處理的事件的清單。
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 28%

---

# Places事件參考 {#places-event-reference}

以下為Places擴充功能處理的事件清單。

## GetCurrentPointsOfInterest

**事件詳細資料**

| 類型 | 來源 | 名稱 | 配對 |
| :--- | :--- | :--- | :--- |
| 地標 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**事件說明**

此事件是要求擷取裝置目前所在的POI。

**資料裝載定義**

N/A

## GetNeartherPointsOfInterest

**事件詳細資料**

| 類型 | 來源 | 名稱 | 配對 |
| :--- | :--- | :--- | :--- |
| 地標 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**事件說明**

此事件是取得附近POI的要求，需要考量目前裝置位置和已設定的Places程式庫。

**資料裝載定義**

| 代碼 | 值類型 | 必填 | 預設值 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| latitude | 兩次 | true | N/A | 儲存搜尋附近POI的中心的緯度值。 |
| longitude | 兩次 | true | N/A | 儲存搜尋附近POI的中心的經度值。 |
| 半徑 | 整數 | false | N/A | 搜尋附近POI所使用的半徑（公尺）。 |
| count | 整數 | false | 10 | 產生回應事件時所傳回的POI數量上限。 |

## ProcessRegionEvent

**事件詳細資料**

| 類型 | 來源 | 名稱 | 配對 |
| :--- | :--- | :--- | :--- |
| 地標 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**事件說明**

此事件會讓Places擴充功能處理地理圍欄登入或退出事件。

**資料裝載定義**

| 代碼 | 值類型 | 必填 | 說明 |
| :--- | :--- | :--- | :--- |
| regionid | 字串 | true | 產生事件的地區識別碼。 |
| regioneventtype | int | true | 正在產生的區域事件型別。 1代表進入，2代表退出。 |

## Places擴充功能傳送的事件

此資訊目前正在處理中。
