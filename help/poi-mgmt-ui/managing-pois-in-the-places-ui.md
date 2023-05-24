---
title: 管理現有POI
description: 在Places服務UI中，您可以編輯、刪除或篩選現有POI。
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 6%

---

# 管理現有POI {#managing-existing-pois}

POI和程式庫是使用Places UI在Places資料庫中建立和管理的。

## 編輯POI

1. 使用您的Adobe ID登入地標。
1. 使用您的Adobe ID登入Places服務。
1. 按一下右上角看起來像專案符號清單的圖示。
1. 找到您要編輯的POI。
1. 按一下 **[!UICONTROL ...]** 並選取 **[!UICONTROL 檢視詳細資料]**.
1. 更新資訊並按一下 **[!UICONTROL 儲存]**.

## 刪除POI

1. 使用您的Adobe ID登入地標。
1. 使用您的Adobe ID登入Places服務。
1. 按一下右上角看起來像專案符號清單的圖示。
1. 找到您要刪除的POI。
1. 按一下 **[!UICONTROL ...]** 並選取 **[!UICONTROL 刪除]**.

## 依城市、州/省、國家或中繼資料篩選POI

![篩選POI](/help/assets/filter_poi.png)

1. 使用您的Adobe ID登入Places服務UI。
1. 按一下右上方的篩選圖示。
1. 您可以透過下列其中一種方式來篩選POI：

   * 依程式庫：

      a.選取程式庫。

   * 依屬性：

      a.在「屬性」下拉式清單中，選取 **[!UICONTROL 國家]**， **[!UICONTROL 州]**，或 **[!UICONTROL 城市]**.

      b.在下一行，輸入值。

      例如，您可以選取 **[!UICONTROL 州]** 和型別 **[!UICONTROL 加州]**.

   * 含中繼資料：

      a.輸入索引鍵和值。

## 定義地理圍欄POI

地理圍欄是一種POI，在資料庫中根據以下索引鍵定義：

| 金鑰 | 說明 | 必填？ |
| :--- | :--- | :--- |
| ID | 指派給每個POI的唯一識別碼 | 是 |
| 名稱 | 為POI指定的易記名稱。 | 是 |
| 資料庫 | 必須為每個POI指派組織資料庫。 | 是 |
| 半徑 | 您的POI半徑（公尺）。 | 是 |
| 圖示 | 協助進行POI的視覺化。 | 是（指派預設值） |
| 色彩 | 協助進行POI的視覺化。 | 是（指派預設值） |
| 類別 | 指派在所有資料庫中所有POI通用的類別共同架構。 | 無 |
| 位址 | 街道地址. | 無 |
| 城市 | POI的城市。 | 無 |
| 州/省/地區 | POI的州或地區。 | 無 |
| 國家/地區 | POI的國家/地區。 | 無 |
| 緯度 | POI中心的緯度座標。 | 是 |
| 經度 | POI中心的經度座標。 | 是 |
| 中繼資料 | 可指派給POI的自訂索引鍵和值配對。 此中繼資料可讓您跨資料庫為每個將POI分組，以便在下游工作流程中使用規則和篩選器，例如當有人使用「型別=競爭者」輸入POI時傳送推播通知，藉此簡化未來的工作流程。 | 無 |
