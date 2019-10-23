---
title: 建立程式庫
seo-title: 建立程式庫
description: 使用Places REST API建立資料庫。
seo-description: 使用Places REST API建立資料庫。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# 建立程式庫

可讓您建立程式庫的POST方法。

## 請求

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## 標題

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 內文

```text
{"name": "<LIBRARY_NAME>"}
```

## 範例回應

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL命令

使用下列CURL命令測試此API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>以實際值 `<API KEY>`取代 `<TOKEN>`變 `<ORGID>` 數，例如、和。

