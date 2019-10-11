---
title: 刪除POI
seo-title: 刪除POI
description: 使用Places REST API刪除POI。
seo-description: 使用Places REST API刪除POI。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 刪除POI

可讓您刪除POI的DELETE方法。

## 請求

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
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
If successful a Status of "204 No Content" is returned.
```

## CURL命令

使用下列CURL命令測試API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>以實 `<POIID>`際值 `<API KEY>`取代 `<TOKEN>`、、 `<ORGID>` 和。

