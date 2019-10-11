---
title: 在Places UI中管理POI
seo-title: 在Places UI中管理POI
description: 使用「地標」UI管理您的POI。
seo-description: 使用「地標」UI管理您的POI。
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# 在Places UI中管理POI

POI和庫是使用Places UI在Places資料庫中建立和管理的。

## 定義地理序列POI

Geoffences是POI的一種類型，在資料庫中按以下鍵定義：

| 密鑰 | 說明 | 必填? |
| :--- | :--- | :--- |
| ID | 分配給每個POI的唯一標識符 | 是 |
| 名稱 | 為POI提供好記名稱 | 是 |
| 庫 | 每個POI都必須指派一個程式庫供組織使用 | 是 |
| 圖示 | 協助POI的視覺化 | 是（已指派預設值） |
| 色彩 | 協助POI的視覺化 | 是（已指派預設值） |
| 類別 | 為所有資料庫中所有POI指派共同的類別架構 | 無 |
| 地址 | 街道地址 | 無 |
| 城市 | POI市 | 無 |
| 省/地區 | POI的州或地區 | 無 |
| 國家 | POI國家 | 無 |
| 緯度 | POI中心的緯度坐標 | 是 |
| 經度 | POI中心的經度坐標 | 是 |
| 中繼資料 | 可指派給POI的自訂金鑰+值配對。 此中繼資料可讓您跨資料庫將POI分組，讓每個POI在下游工作流程中使用規則和篩選器，例如每當有人輸入「類型=競爭者」的POI時傳送推播通知。 | 無 |

## 建立 POI {#create-a-poi}

興趣點(POI)是您感興趣的地圖上的位置或點。 酒店可以包括咖啡館、餐館等地。

1. 使用您的Adobe ID登入Adobe Places。
2. 在右上方，按一下看起來像項目清單的圖示，然後按一下 **[!UICONTROL New]**。
3. 鍵入POI的名稱。
4. 選取或新增資料庫。
5. 輸入或選擇半徑。

   a.為您的POI選取圖示。
b.b.為表徵圖選擇顏色。

6. 展開該 **[!UICONTROL Location]** 部分。

   a.輸入地址。

   b.輸入城市。

   c.鍵入狀態名稱。

   d.鍵入國家／地區的名稱。

   e.選擇或輸入緯度或經度。

   f.按一 **[!UICONTROL Drop Pin on Map]**&#x200B;下。

7. 展開該 **[!UICONTROL Metadata]** 部分並按一下 **[!UICONTROL Add Metadata]**。

   a.鍵入鍵名。

   b.鍵入鍵值。

8. 按一 **[!UICONTROL Confirm]** 下然後 **[!UICONTROL  Save]**。

## 編輯POI

1. 使用您的Adobe ID登入「地標」。
1. 使用您的Adobe ID登入Adobe Places服務。
1. 在右上方，按一下類似項目清單的圖示。
1. 找出您要編輯的POI。
1. 按一 **[!UICONTROL ...]** 下並選取 **[!UICONTROL View Details]**。
1. 更新資訊，然後按一下 **[!UICONTROL Save]**。

## 刪除POI

1. 使用您的Adobe ID登入「地標」。
1. 使用您的Adobe ID登入Adobe Places服務。
1. 在右上方，按一下類似項目清單的圖示。
1. 找到要刪除的POI。
1. 按一 **[!UICONTROL ...]** 下並選取 **[!UICONTROL Delete]**。

## 依城市、州、國家或中繼資料篩選POI

1. 使用您的Adobe ID登入Adobe Places服務。
1. 在右上方，按一下篩選圖示。
1. 您可透過下列其中一種方式來篩選POI:

   * 依資料庫：

      a.選取資料庫。

   * 依屬性：

      a.在屬性下拉式清單中，選 **[!UICONTROL Country]**&#x200B;取、 **[!UICONTROL State]**&#x200B;或 **[!UICONTROL City]**。

      b.在下一行中，輸入一個值。

      例如，您可以選取並 **[!UICONTROL State]** 輸入 **[!UICONTROL California]**。

   * 使用中繼資料：

      a.輸入鍵和值。

