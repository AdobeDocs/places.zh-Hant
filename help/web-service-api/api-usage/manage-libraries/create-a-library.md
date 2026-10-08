---
title: 建立程式庫
description: 使用Places REST API建立程式庫。
exl-id: 155cc6e6-9254-4389-bb02-e526d15908f4
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 18%
---
# 建立程式庫 {#create-a-library}

可讓您建立程式庫的POST方法。

## 請求

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## 標頭

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

## CURL指令

使用下列CURL命令來測試此API：

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>將`<API KEY>`、`<TOKEN>`和`<ORGID>`等變數取代為實際值。
