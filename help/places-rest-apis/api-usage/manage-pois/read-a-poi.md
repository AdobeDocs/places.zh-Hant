---
title: 閱讀POI
seo-title: 閱讀POI
description: 使用Places REST API讀取POI。
seo-description: 使用Places REST API讀取POI。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 閱讀POI

返回POI詳細資訊的GET方法。

## 請求

```text
GET https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## 標題

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## 範例回應

```text
{
    "id": "66e3c0fb-12fe-4af2-863e-16e0e578d777",
    "name": "Train Station Road",
    "description": "18827",
    "location": {
        "type": "Point",
        "coordinates": [
            -121.902498,
            37.331087
        ]
    },
    "radius": 66,
    "country": "PH",
    "state": "41",
    "city": "Quezon City",
    "street": "No. 10 Train Station Road",
    "category": "",
    "icon": "",
    "color": "",
    "metadata": {
        "ownership": "LS",
        "brand": "Train station"
    },
    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"
}
```

## CURL命令

使用下列CURL命令測試API:

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>以實 `<POIID>`際值 `<API KEY>`取代 `<TOKEN>`、、 `<ORIGIN>` 和。

