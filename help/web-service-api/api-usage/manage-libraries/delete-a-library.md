---
title: 刪除程式庫
description: 使用Places REST API刪除程式庫。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 6%

---


# 刪除程式庫 {#delete-a-library}

可讓您刪除程式庫的DELETE方法。

## 請求

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

使用下列CURL命令測試此API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>以實際值取 `<lIBRARYID>`代 `<API KEY>`、 `<TOKEN>`和等 `<ORGID>`變數。

