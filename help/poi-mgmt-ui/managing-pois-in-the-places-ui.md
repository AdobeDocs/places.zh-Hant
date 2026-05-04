---
title: 管理現有POI
description: 在Places Service UI中，您可以編輯、刪除或篩選現有POI。
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
TQID: https://experienceleague.adobe.com/2VnBQ5-flpx5cyeK3n5b3AOKqnt7RVkdqFBXYa9O5Ys
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 408
ht-degree: 6%

---

# 管理現有POI {#managing-existing-pois}

POI和程式庫是使用Places UI在Places資料庫中建立和管理的。

## 編輯POI

1. 使用您的Adobe ID登入地標。
1. 使用您的Adobe ID登入Places服務。
1. 按一下右上角看起來像專案符號清單的圖示。
1. 找到您要編輯的POI。
1. 按一下&#x200B;**[!UICONTROL ...]**&#x200B;並選取&#x200B;**[!UICONTROL 檢視詳細資料]**。
1. 更新資訊，然後按一下&#x200B;**[!UICONTROL 儲存]**。

## 刪除POI

1. 使用您的Adobe ID登入地標。
1. 使用您的Adobe ID登入Places服務。
1. 按一下右上角看起來像專案符號清單的圖示。
1. 找到您要刪除的POI。
1. 按一下&#x200B;**[!UICONTROL ...]**&#x200B;並選取&#x200B;**[!UICONTROL 刪除]**。

## 依城市、州、國家或中繼資料篩選POI

![篩選POI](/help/assets/filter_poi.png)

1. 使用您的Adobe ID登入Places服務UI。
1. 按一下右上方的篩選圖示。
1. 您可以透過下列其中一種方式來篩選POI：

   * 依程式庫：

     答： 選取程式庫。

   * 依屬性：

     答： 在「屬性」下拉式清單中，選取&#x200B;**[!UICONTROL 國家]**、**[!UICONTROL 州]**&#x200B;或&#x200B;**[!UICONTROL 城市]**。

     b. 在下一行中輸入值。

     例如，您可以選取&#x200B;**[!UICONTROL 州]**&#x200B;並輸入&#x200B;**[!UICONTROL 加州]**。

   * 包含中繼資料：

     答： 輸入索引鍵和值。

## 定義地理圍欄POI

地理圍欄是一種POI，並在資料庫中根據以下索引鍵定義：

| 索引鍵 | 說明 | 必要? |
| :--- | :--- | :--- |
| ID | 指派給每個POI的唯一識別碼 | 是 |
| 名稱 | 為POI指定的易記名稱。 | 是 |
| 資料庫 | 必須為每個POI指派組織資料庫。 | 是 |
| 半徑 | 您的POI半徑（公尺）。 | 是 |
| 圖示 | 協助進行POI的視覺化。 | 是（指派預設） |
| 顏色 | 協助進行POI的視覺化。 | 是（指派預設） |
| 類別 | 指派在所有資料庫中所有POI通用的類別共同架構。 | 無 |
| 地址 | 街道地址。 | 無 |
| 城市 | POI的城市。 | 無 |
| 州/省/地區 | POI所在州或地區。 | 無 |
| 國家/地區 | POI的國家/地區。 | 無 |
| 緯度 | POI中心的緯度座標。 | 是 |
| 經度 | POI中心的經度座標。 | 是 |
| 中繼資料 | 可指派給POI的自訂索引鍵和值配對。 此中繼資料可讓您跨資料庫將POI分組，以供每個在下游工作流程中使用規則和篩選器，例如當有人使用「型別=競爭者」輸入POI時傳送推播通知，藉此簡化未來的工作流程。 | 無 |
