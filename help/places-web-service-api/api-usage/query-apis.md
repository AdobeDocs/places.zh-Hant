---
title: 概述
seo-title: 查詢API
description: 瞭解和使用查詢API。
seo-description: 瞭解和使用查詢API。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# 查詢API

一種GET方法，可讓您查詢離呼叫者最近的POI。

## 請求

```text
GET https://query.places.adobe.com/placesedgequery
```

在以下輸入中，服務返回最接近呼叫者的POI清單：

* 呼叫者的位置\（緯度、經度\）。
* 要包含在搜尋中的POI程式庫ID。
* 要返回的最大POI數。  預設值為 100。

   呼叫者與POI之間的距離定義為從呼叫者到POI地理位置邊緣的距離。 在響應中，包含呼叫者的POI將被標籤為具有呼叫者。

參數作為以下查詢參數提供：

* (**必填**) `latitude`

   呼叫者的緯度，必須介於-85和85之間。
* (**必填**) `longitude`

   呼叫者的經度，必須介於-180和180之間。

* (**可選**) `limit`

   要返回的最大POI數。

* (**必填**) `library`

   要查詢的庫的ID。 若要查詢多個程式庫，請確定您在查詢中包含多個程式庫參數副本。

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

下面的POI `places.pois` 按呼叫者到POI邊緣的距離排序。 POI下包 `places.userWithin` 含呼叫者，這些POI依排名排序，然後依半徑增加排序。

## 範例呼叫

以下是此呼叫的範例：

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
