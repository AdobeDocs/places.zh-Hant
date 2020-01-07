---
title: 在「地標」UI中管理程式庫
description: 使用「地標」UI管理您的資料庫。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Manage libraries {#manage-libraries-places-ui}

資料庫是POI的集合。 資料庫中最多可有150,000個POI，而每個Experience cloud組織最多可有100個資料庫。

有多種方式可將POI組織到資料庫，視組織最有用的項目而定。 有些客戶可能偏好為每個行動應用程式建立個別的資料庫，而其他客戶則可能會使用資料庫來將特定類型的POI（例如咖啡店、公園、酒店等）分組。 例如，一家大型娛樂公司可能有一個圖書館，其室外場所位於一個圖書館，零售商店位於另一個圖書館。 市政府可能會有一個圖書館，它包含了市內所有的建築，還有一個圖書館，它包含了市內所有的公園。

程式庫由下列項目定義：

| 密鑰: | 說明: |
| :--- | :--- |
| ID | 建立時指派給程式庫的唯一識別碼 |
| 名稱 | 給圖書館的好記名字 |
| 排名 | 如果您的組織中沒有重疊的地理位置，則可忽略這些排名。 如果有重疊的 POI，則建議您將每個地理柵欄放在不同的資料庫中，以便地理柵欄能相對地互相加權。使用者一次只能處於一個地理柵欄中。<br><br>使用者所在地理柵欄的最高排名，決定了其目前的地理柵欄會籍。如果有地理柵欄的資料庫排名相同，則最小的地理柵欄是使用者目前的地理柵欄。<br><br>SDK也會得知「上次輸入 *」和「上次退出*** 」POI，因此您完全可以根據使用者與POI的互動來控制觸發規則的方式。 |

## 建立程式庫

1. 使用您的Adobe ID登入「地標」。
1. 在右上方，按一下 **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**。
1. 按一下 **[!UICONTROL New]**。
1. 鍵入名稱。
1. 按一下 **[!UICONTROL Confirm]**。

## 在「地標」UI中變更資料庫的排名

1. 使用您的Adobe ID登入「地標」。
1. 在右上方，按一下 **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**。
1. 按一下程式庫名稱左側的圖示，並將程式庫拖曳至新排名。

## 重新命名資料庫

1. 使用您的Adobe ID登入「地標」。
1. 在右上方，按一下 **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**。
1. 找到您要刪除的程式庫。
1. 按一 **[!UICONTROL ...]**下並選取**[!UICONTROL Rename]**。
1. 更新名稱，然後按一下 **[!UICONTROL Save]**。

## 刪除程式庫

1. 使用您的Adobe ID登入「地標」。
1. 在右上方，按一下 **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**。
1. 找到您要刪除的程式庫。
1. 按一 **[!UICONTROL ...]**下並選取**[!UICONTROL Delete]**。

