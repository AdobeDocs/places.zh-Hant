---
title: 刪除多個POI
seo-title: 刪除多個POI
description: 使用批次API刪除多個POI。
seo-description: 使用批次API刪除多個POI。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# 刪除多個POI {#delete-multiple-pois}

可讓您刪除多個POI的POST方法。

## 請求

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## 標題

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

## CURL命令

使用下列CURL命令測試此API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>以實 `<API KEY>`際值 `<TOKEN>`來取 `<ORGID>`代、 `<PATHTOBATCHDELETEJSONFILE>` 取代和。

## 範例JSON檔案

以下是 `batchDelete` API的範例JSON檔案：

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
