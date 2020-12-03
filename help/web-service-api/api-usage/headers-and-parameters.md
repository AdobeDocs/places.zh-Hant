---
title: 標題和參數
description: Places Service REST API中可用的標題和參數。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 11%

---


# Headers and parameters {#headers-and-parameters}

以下是Places Service REST API中可用標題和參數的詳細資訊：

## 支援的標題

| Header | 說明 | 方法 | 範例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | 您的持牌代號 | 全部 |  |
| `x-api-key` | 您的API金鑰 | 全部 | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 您的組織ID | 全部 | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 傳送或接收的內容格式 | PUT, POST | `application/json` |
| `Accept-Language` | 用於錯誤消息的語言 | 選填 | `en-US` |

## 程式庫參數

| 參數 | 說明 | 類型 | 限制 | 請求或回應 | 範例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | 資料庫的ID | 已分配 | n/a | 回應 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | 程式庫的名稱 | 字串 | 256 個字元 | 兩者皆需，請求中需要 | `"name": "Amazing Places"` |
| `orgID` | 組織的Experience Cloud組織ID | 已分配 | n/a | 回應 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | 圖書館的POI數量 | 整數 | 最大150,000 | 回應 | `"poiCount": 25149` |
| `metadataDescriptors` | 計算每個唯一的POI元資料鍵值對 | 混合 | n/a | 回應 |  |
| `poiCountInCities` | 計算每個唯一的POI城市值 | 混合 | n/a | 回應 |  |

## POI參數

| 參數 | 說明 | 類型 | 限制 | 請求或回應 | 範例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi資料 | POI詳細資訊陣列 | n/a | both |  |
| `id` | POI的ID | 已分配 | n/a | 響應 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POI的名稱 | 字串 | 512 個字元 | 兩者皆可，可選\* | `"name": "My Favorite Place"` |
| `description` | POI的說明 | 字串 | 512 個字元 | 兩者皆可，可選\* | `"description": "This is a very good place."` |
| `location` | POI的類型與座標陣列 | 陣列（混合） | n/a | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI類型 | 字串 | 目前僅支援&quot;Point&quot; | 兩者皆需，請求中需要 | `"type": "Point"` |
| `coordinates` | POI的經緯度陣列 | 陣列（浮點） | 經度：-180到180,latitude -85到85 | 兩者皆需，請求中需要 | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI周圍圓形地震的大小 | 浮水 | 10 - 2000米 | 兩者皆需，請求中需要 | `"radius": 100` |
| `country` | POI的國家／地區 | 字串 | 32 個字元 | both, optional* | `"country": "United States"` |
| `state` | POI的狀態 | 字串 | 32 個字元 | both, optional* | `"state": "California"` |
| `city` | POI的城市 | 字串 | 32 個字元 | both, optional* | `"city": "San Jose"` |
| `street` | POI的街道地址 | 字串 | 256 個字元 | both, optional* | `"street": "122 Woz Way"` |
| `category` | POI的類別 | 字串 | 100 個字元 | both, optional* | `"category": "cafe"` |
| `icon` | POI的圖示 | 字串 | 50 個字元 | both, optional* | `"icon": "star"` |
| `color` | POI的色彩 | 字串 | 8 個字元 | both, optional* | `"color": "blue"` |
| `metadata` | POI的鍵／值對陣列 | array(string) | 鍵：256個字元，值：256個字元，最多10對 | both, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POI所在的庫ID | n/a | n/a | both, required | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* 如果未包括參數值，則該值將設定為在數 `empty` 據庫中。 如果不包括現有的鍵／值對，則會為資料庫中該POI刪除鍵／值對。

