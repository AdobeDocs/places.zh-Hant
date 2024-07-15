---
title: 刪除多個POI
description: 使用批次API來刪除多個POI。
exl-id: f170b722-e6f4-42a2-b3a6-1bf56965eb17
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 5%

---

# 刪除多個POI {#delete-multiple-pois}

可讓您刪除多個POI的POST方法。

## 請求

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## 標頭

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 內文

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## 範例回應

```text
If successful a Status of "204 No Content" is returned.
```

## CURL指令

使用下列CURL命令來測試此API：

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>將`<API KEY>`、`<TOKEN>`、`<ORGID>`和`<PATHTOBATCHDELETEJSONFILE>`取代為實數值。

## 範例JSON檔案

以下是`batchDelete` API的範例JSON檔案：

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
