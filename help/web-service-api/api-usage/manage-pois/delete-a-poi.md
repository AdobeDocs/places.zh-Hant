---
title: 刪除POI
description: 使用Places REST API刪除POI。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 6%

---


# 刪除POI {#delete-a-poi}

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

