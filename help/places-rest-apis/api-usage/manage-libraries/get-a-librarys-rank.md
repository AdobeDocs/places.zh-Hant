---
title: 取得資料庫的排名
seo-title: 取得資料庫的排名
description: 使用Places REST API取得資料庫的排名。
seo-description: 使用Places REST API取得資料庫的排名。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 取得資料庫的排名

一種GET方法，可讓您對程式庫排名。

## 請求

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## 標題

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## 範例回應

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURL命令

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>以實際值 `<API KEY>`取代 `<TOKEN>`變 `<ORGID>` 數，例如、和。

