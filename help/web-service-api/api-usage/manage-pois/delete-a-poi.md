---
title: 刪除POI
description: 使用Places REST API刪除POI。
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 4%

---

# 刪除POI {#delete-a-poi}

可讓您刪除POI的DELETE方法。

## 請求

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## 標頭

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

## CURL指令

使用下列CURL命令來測試API：

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>將`<POIID>`、`<API KEY>`、`<TOKEN>`和`<ORGID>`取代為實際值。
