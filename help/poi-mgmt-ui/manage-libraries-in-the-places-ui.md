---
title: 在Places服務UI中管理程式庫
description: 使用Places Service UI管理您的程式庫。
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
TQID: https://experienceleague.adobe.com/PP7P3aOL3EKSEPJWedHtfyHRzbCueMtNS-J7Ao4mawo
product_v2: id: cb954087-f4fc-4456-afb9-e939cabcdc79id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 434
ht-degree: 14%

---

# 管理程式庫 {#manage-libraries-places-ui}

資料庫是POI的集合。 資料庫中最多可以有150,000個POI，而每個Experience Cloud組織最多可以有100個資料庫。

根據對組織最有用的內容，有多種方式可將POI整理到資料庫中。 有些客戶可能偏好為每個行動應用程式建立個別的資料庫，有些客戶則可能會使用資料庫將特定型別的POI分組，例如咖啡館、公園、飯店等。 例如，一家大型娛樂公司可能有一個圖書館，其中包含一家圖書館內的戶外場所，以及另一家圖書館內的零售店。 一個市政府可能有一個包含市內所有建築的圖書館，另一個包含市內所有公園的圖書館。

程式庫由下列專案定義：

| 索引鍵： | 說明： |
| :--- | :--- |
| ID | 建立時指派給程式庫的唯一識別碼 |
| 名稱 | 為程式庫指定的易記名稱 |
| 排名 | 如果您的組織中沒有重疊的地理柵欄，則會忽略這些排名。 如果有重疊的 POI，則建議您將每個地理柵欄放在不同的資料庫中，以便地理柵欄能相對地互相加權。 使用者一次只能處於一個地理柵欄中。 <br><br>使用者所在地理柵欄的最高排名，決定了其目前的地理柵欄會籍。 如果有地理柵欄的資料庫排名相同，則最小的地理柵欄是使用者目前的地理柵欄。 <br><br>SDK也會得知&#x200B;*上次進入*&#x200B;和&#x200B;*上次退出*&#x200B;個POI，因此您可以完全控制要如何根據使用者與POI的互動來觸發規則。 |

## 建立程式庫

1. 使用您的Adobe ID登入地標。
1. 按一下右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理資料庫]**。
1. 按一下&#x200B;**[!UICONTROL 「新增」]**。
1. 輸入名稱。
1. 按一下「**[!UICONTROL 確認]**」。

## 變更Places使用者介面中資料庫的排名

1. 使用您的Adobe ID登入地標。
1. 按一下右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理資料庫]**。
1. 按一下資料庫名稱左側的圖示，然後將資料庫拖曳至新排名。

## 重新命名資料庫

1. 使用您的Adobe ID登入地標。
1. 按一下右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理資料庫]**。
1. 找到您要刪除的程式庫。
1. 按一下&#x200B;**[!UICONTROL ...]**&#x200B;並選取&#x200B;**[!UICONTROL 重新命名]**。
1. 更新名稱並按一下&#x200B;**[!UICONTROL 儲存]**。

## 刪除程式庫

1. 使用您的Adobe ID登入地標。
1. 按一下右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理資料庫]**。
1. 找到您要刪除的程式庫。
1. 按一下&#x200B;**[!UICONTROL ...]**&#x200B;並選取&#x200B;**[!UICONTROL 刪除]**。
