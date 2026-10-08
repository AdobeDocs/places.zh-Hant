---
title: 建立POI
description: 使用Places REST API建立POI。
exl-id: 0f5b5b40-11f0-4122-b3d5-c3853a6e8ca5
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 6%
---
# 建立POI {#create-a-poi}

允許您建立POI的POST方法。

## 請求

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois
```

## 標頭

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## 內文

```text
{
  "name": "string",
  "description": "string",
  "location": {
    "type": Point",
    "coordinates": [<LONGITUDE>, <LATITUDE>]
  },
  "radius": radius,
  "country": "string",
  "state": "string",
  "city": "string",
  "street": "string",
  "category": "string",
  "icon": "string",
  "color": "string",
  "metadata": {
          "brand": "string",
          "owndership": "string",
          "Color": "string"
  },
  "lib_id": "{libraryID}"
}
```

## 範例回應

```text
{
    "id": "66e3c0fb-12fe-4af2-863e-16e0e777d777",
    "name": "New POI",
    "description": "18827",
    "location": {
        "type": "Point",
        "coordinates": [
            -123.000507,
            37.698029
        ]
    },
    "radius": 66,
    "country": "US",
    "state": "CA",
    "city": "Small City",
    "street": "1 Island Road",
    "category": "",
    "icon": "",
    "color": "",
    "metadata": {
        "ownership": "LS",
        "brand": "Island station"
    },
    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"
}
```

## CURL指令

使用下列CURL命令來測試此API：

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '<SINGLEPOIDATA>' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>記得要以實際值取代`<API KEY>`、`<TOKEN>`、&#39;，&#39;和`<SINGLEPOIDATA>`。
