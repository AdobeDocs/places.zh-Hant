---
title: 地點事件參考
description: '由「地標」擴充功能處理的事件清單。 '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---


# 地點事件參考 {#places-event-reference}

以下是由「地標」擴充功能處理的事件清單。

## GetCurrentPointsOfInterest

**事件詳細資料**

| 類型 | 來源 | 名稱 | 配對 |
| :--- | :--- | :--- | :--- |
| 地標 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**事件說明**

此事件是請求擷取裝置目前所在的POI。

**資料裝載定義**

n/a

## GetOnnexterPointsOfInterest

**事件詳細資料**

| 類型 | 來源 | 名稱 | 配對 |
| :--- | :--- | :--- | :--- |
| 地標 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**事件說明**

此事件是要求您考慮目前裝置位置和已設定的Places程式庫，以取得附近的POI。

**資料裝載定義**

| 代碼 | 值類型 | 必填 | 預設值 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| latitude | 雙倍 | true | n/a | 保留搜索附近POI中心的緯度值。 |
| longitude | 雙倍 | true | n/a | 保存附近POI搜索中心的經度值。 |
| 半徑 | 整數 | false | n/a | 半徑（以米為單位），用於搜索附近的POI。 |
| count | 整數 | false | 10 | 在結果回應事件中返回的POI的最大數量。 |

## ProcessRegionEvent

**事件詳細資料**

| 類型 | 來源 | 名稱 | 配對 |
| :--- | :--- | :--- | :--- |
| 地標 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**事件說明**

此事件會使「地標」延伸模組處理地標進入或退出事件。

**資料裝載定義**

| 代碼 | 值類型 | 必填 | 說明 |
| :--- | :--- | :--- | :--- |
| regionid | 字串 | true | 產生事件之地區的ID。 |
| regioneventtype | int | true | 正在產生的地區事件類型。 1代表進入，2代表退出。 |

## Places延伸功能所傳送的事件

此資訊目前正在進行中。

