---
title: 閱讀組織中的所有資料庫
seo-title: 閱讀組織中的所有資料庫
description: 使用Places REST API讀取組織中的所有資料庫。
seo-description: 使用Places REST API讀取組織中的所有資料庫。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# 閱讀組織中的所有資料庫

一種GET方法，可傳回組織中所有程式庫的詳細資料。

## 請求

```text
GET https://api-places.adobe.io/places/placesapi/v1/libraries
```

## 標題

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 範例回應

```text
[    {        "id": "5abb5c6d-ce4f-43f3-a253-120ae883777f",        "name": "Restaurants",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 1    },    {        "id": ""9aa7f663-35cc-4de6-8643-ae7779f3bb87",        "name": "Gas stations",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 30    },    {        "id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777",        "name": "Coffee shops",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 25151    },    {        "id": "d1330287-79bd-44fb-b777-5e59ec37faad",        "name": "Theatres",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 0    }]
```

## CURL命令

使用下列CURL命令測試此API:

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>以實際值取 `<API KEY>`代 `<TOKEN>,``<ORGID>` 變數，例如。