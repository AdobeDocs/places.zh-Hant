---
title: 總覽
description: 瞭解和使用查詢API。
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 4%

---

# 查詢API

一種GET方法，可讓您查詢最靠近呼叫者的POI。

## 請求

```text
GET https://query.places.adobe.com/placesedgequery
```

透過下列輸入，服務會傳回最接近呼叫者的POI清單：

* 呼叫者的位置（經緯度）。
* 要包含在搜尋中的POI資料庫ID。
* 要傳回的POI數量上限。  預設值為 100。

   呼叫者與POI之間的距離定義為呼叫者到POI地理圍欄邊緣的距離。 在回應中，包含來電者的POI將會標示為具有來電者。

提供引數作為下列查詢引數：

* (**必填**) `latitude`

   來電者的緯度，必須介於–85到85之間。
* (**必填**) `longitude`

   呼叫者的經度，必須介於–180到180之間。

* (**選擇性**) `limit`

   要傳回的POI數量上限。

* (**必填**) `library`

   要查詢的資料庫ID。 若要查詢多個程式庫，請確保在查詢中包含多個程式庫引數副本。

以下是成功傳回JSON格式的範例：

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

POI位於 `places.pois` 是以呼叫者與POI邊緣的距離排序。 POI位於 `places.userWithin` 包含呼叫者，而這些POI會先依排名排序，然後依半徑增加排序。

## 呼叫範例

以下是呼叫的範例：

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
