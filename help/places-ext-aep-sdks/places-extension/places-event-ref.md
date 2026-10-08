---
title: Places事件參考
description: Places擴充功能處理的事件清單。
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 17%
---
# Places事件參考 {#places-event-reference}

以下為Places擴充功能處理的事件清單。

## GetCurrentPointsOfInterest

**事件詳細資料**

| 類型 | 來源 | 名稱 | 已配對 |
| :--- | :--- | :--- | :--- |
| 地點 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**事件描述**

此事件是擷取裝置目前所在之POI的要求。

**資料裝載定義**

不適用

## GetInnearlyPointsOfInterest

**事件詳細資料**

| 類型 | 來源 | 名稱 | 已配對 |
| :--- | :--- | :--- | :--- |
| 地點 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**事件描述**

此事件是取得附近POI的要求，需要考量目前裝置位置和已設定的Places程式庫。

**資料裝載定義**

| 索引鍵 | 值型別 | 必要 | 預設值 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| latitude | 雙精度浮點數 | 真 | 不適用 | 儲存搜尋附近POI的中央緯度值。 |
| 經度 | 雙精度浮點數 | 真 | 不適用 | 儲存附近POI搜尋中心的經度值。 |
| 半徑 | 整數 | 假 | 不適用 | 搜尋附近POI所使用的半徑（公尺）。 |
| 計數 | 整數 | 假 | 10 | 在產生的回應事件中傳回的POI數量上限。 |

## ProcessRegionEvent

**事件詳細資料**

| 類型 | 來源 | 名稱 | 已配對 |
| :--- | :--- | :--- | :--- |
| 地點 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**事件描述**

此事件會導致Places擴充功能處理地理圍欄登入或退出事件。

**資料裝載定義**

| 索引鍵 | 值型別 | 必要 | 說明 |
| :--- | :--- | :--- | :--- |
| regionid | 字串 | 真 | 產生事件的地區識別碼。 |
| regioneventtype | int | 真 | 正在產生的區域事件型別。 1代表登入，2代表退出。 |

## Places擴充功能傳送的事件

此資訊目前正在處理中。
