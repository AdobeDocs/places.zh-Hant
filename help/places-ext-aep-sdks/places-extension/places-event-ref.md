---
title: 地點事件參考
seo-title: 地點事件參考
description: '由「地標」擴充功能處理的事件清單。 '
seo-description: '由「地標」擴充功能處理的事件清單。  '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

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

不適用

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
| 緯度 | 雙倍 | true | 不適用 | 保留搜索附近POI中心的緯度值。 |
| 經度 | 雙倍 | true | 不適用 | 保存附近POI搜索中心的經度值。 |
| 半徑 | 整數 | false | 不適用 | 半徑（以米為單位），用於搜索附近的POI。 |
| 計數 | 整數 | false | 10 | 在結果回應事件中返回的POI的最大數量。 |

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
| regionid | string | true | 產生事件之地區的ID。 |
| regioneventtype | int | true | 正在產生的地區事件類型。 1代表進入，2代表退出。 |

## Places延伸模組所傳送的事件

此資訊目前正在進行中。

