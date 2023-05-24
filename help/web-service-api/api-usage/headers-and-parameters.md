---
title: 標題和引數
description: Places服務REST API中可用的標題和引數。
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 17%

---

# 標題和引數 {#headers-and-parameters}

以下是Places Service REST API中可用標頭和引數的詳細資訊：

## 支援的標頭

| 標頭 | 說明 | 方法 | 範例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | 您的持有人權杖 | 全部 |  |
| `x-api-key` | 您的API金鑰 | 全部 | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 您的組織ID | 全部 | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 傳送或接收的內容格式 | PUT，POST | `application/json` |
| `Accept-Language` | 用於錯誤訊息的語言 | 選填 | `en-US` |

## 程式庫引數

| 參數 | 說明 | 類型 | 限制 | 要求或回應 | 範例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | 資料庫ID | 已指派 | N/A | 回應 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | 程式庫名稱 | 字串 | 256 個字元 | 兩者皆有，為請求所必需 | `"name": "Amazing Places"` |
| `orgID` | 組織的Experience Cloud orgID | 已指派 | N/A | 回應 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | 資料庫中的POI數量 | 整數 | 最多150,000個 | 回應 | `"poiCount": 25149` |
| `metadataDescriptors` | 每個唯一POI中繼資料索引鍵值組的計數 | 混合 | N/A | 回應 |  |
| `poiCountInCities` | 每個唯一POI城市值的計數 | 混合 | N/A | 回應 |  |

## POI引數

| 參數 | 說明 | 類型 | 限制 | 要求或回應 | 範例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi資料 | POI詳細資訊陣列 | N/A | 兩者 |  |
| `id` | POI ID | 已指派 | N/A | 回應 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POI的名稱 | 字串 | 512 個字元 | 兩者，選用\* | `"name": "My Favorite Place"` |
| `description` | POI的說明 | 字串 | 512 個字元 | 兩者，選用\* | `"description": "This is a very good place."` |
| `location` | POI的型別與座標陣列 | 陣列（混合） | N/A | 兩者 | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI型別 | 字串 | 目前僅支援「點」 | 兩者皆有，為請求所必需 | `"type": "Point"` |
| `coordinates` | POI的經度和緯度陣列 | 陣列（浮點數） | 經度：-180至180，緯度–85至85 | 兩者皆有，為請求所必需 | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI周圍圓形地理圍欄的大小 | 浮點數 | 10 - 2000米 | 兩者皆有，為請求所必需 | `"radius": 100` |
| `country` | POI的國家/地區 | 字串 | 32 個字元 | 兩者，選擇性* | `"country": "United States"` |
| `state` | POI的州 | 字串 | 32 個字元 | 兩者，選擇性* | `"state": "California"` |
| `city` | POI的城市 | 字串 | 32 個字元 | 兩者，選擇性* | `"city": "San Jose"` |
| `street` | POI的街道地址 | 字串 | 256 個字元 | 兩者，選擇性* | `"street": "122 Woz Way"` |
| `category` | POI的類別 | 字串 | 100 個字元 | 兩者，選擇性* | `"category": "cafe"` |
| `icon` | POI圖示 | 字串 | 50 個字元 | 兩者，選擇性* | `"icon": "star"` |
| `color` | POI的色彩 | 字串 | 8 個字元 | 兩者，選擇性* | `"color": "blue"` |
| `metadata` | POI的索引鍵/值組陣列 | array(string) | 索引碼：256個字元，值：256個字元，最多10對 | 兩者，選擇性* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POI所在的資料庫ID | N/A | N/A | 兩者，必填 | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* 如果未包含引數值，則值會設為 `empty` 在資料庫中。 如果未包含現有的索引鍵/值組，則會移除資料庫中該POI的索引鍵/值組。
