---
title: 為您的Places Service屬性建立規則
description: Places SDK可追蹤目前位置、監控目前位置周圍已設定的POI，以及追蹤這些POI的進入和退出事件。
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 15%

---

# 建立登入和退出規則 {#create-entry-exit-rules}

行動應用程式中安裝Places擴充功能和區域監控解決方案後，您可以在Adobe Experience Platform Launch中建立觸發或條件式位置資料，包括位置登入和退出事件。

## 規則

您可以設定規則，該規則由事件、條件和動作組成。 每個規則都包含下列專案：

* 一或多個事件
* （選用）條件
* 一或多個動作

### Places Service事件

Places Service提供下列事件，您可以在其上執行規則：

* **輸入POI**，此動作會在客戶進入您設定的POI時由Places SDK觸發。
* **退出POI**，此動作會在客戶退出您設定的POI時由Places SDK觸發。

### Places服務條件

條件會定義與事件相關聯的資料，或該執行個體上擴充功能的共用狀態，必須符合這些條件才能採取動作。 例如，您可以設定條件，只在舊金山City of San Francisco的咖啡店專案上觸發動作。

Places SDK會維護下列狀態：

* 目前POI，代表您客戶目前所在的POI。
* 上次退出的POI，代表您的客戶已退出的最新POI。
* 上次輸入的POI，代表客戶最近輸入的POI。

每個POI都包含以下資料元素：

* ID
* 名稱
* 經緯度
* 半徑
* 城市、國家、州/省、類別等中繼資料

### 動作

動作會定義應用程式在回應引發事件的規則符合條件時，會執行哪些動作。 例如，當您的客戶進入您的POI時，您可以設定歡迎訊息以顯示在其行動裝置上。

## 建立規則：範例

>[!CAUTION]
>
>此範例假設您已建立美國所有咖啡店的 POI 資料庫。如需建立POI和資料庫的詳細資訊，請參閱 [建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md) 和 *建立程式庫* 在 [管理多個程式庫](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

下列程式範例說明如何在您進入舊金山的咖啡廳時，建立將貼文傳回Slack的規則。

事件、條件和動作會以下列方式定義：

* **事件**：Places輸入事件。
* **條件**：**「目前 POI」**&#x200B;的城市是舊金山
* **動作**：傳送回傳以Slack客戶輸入的咖啡館名稱。

### 先決條件

建立規則之前，您必須先在Adobe Experience Platform Launch中建立資料元素。 資料元素會自動在回傳訊息中填入有關您POI的必要資訊。

若要在Experience Platform Launch中建立資料元素：

1. 按一下 **資料元素** 標籤。
1. 按一下&#x200B;**新增資料元素**.
1. 輸入名稱，例如， **目前的咖啡店名稱**.
1. 在 **副檔名** 下拉式清單，選取 **地點 — Beta**.
1. 在&#x200B;**「資料元素」**&#x200B;中，選取&#x200B;**「城市」**。
1. 在右窗格中，選取 **目前的POI**.
1. 按一下&#x200B;**儲存**。

### 為Places Service在Experience Platform Launch中建立規則

![建立規則](/help/assets/placesrule.png)

1. 在 Experience 平台 Launch 中，按一下 **[!UICONTROL 「規則」]**&#x200B;標籤。
1. 按一下&#x200B;**[!UICONTROL 新增規則]**.
1. 輸入規則的名稱，例如， **[!UICONTROL 在SF追蹤咖啡店的入口]**.

### 建立事件

1. 在事件區段中，按一下 **[!UICONTROL +新增]**. 事件會決定您何時要觸發規則。
1. 在 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 地點 — Beta]**.
1. 在&#x200B;**[!UICONTROL 「事件類型」]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 「輸入 POI」]**。
1. 在&#x200B;**[!UICONTROL 「名稱」]**&#x200B;中，輸入事件的名稱，例如 **[!UICONTROL Entering a coffee shop]**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

### 建立條件

1. 在「條件」區段中，按一下 **[!UICONTROL +新增]**. 條件會決定必須符合哪些條件才能採取動作。
1. 在&#x200B;**[!UICONTROL 「邏輯類型」]**&#x200B;中，選取「規則」，以允許在滿足條件時執行動作。
1. 在 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 地點 — Beta]**.
1. 在&#x200B;**[!UICONTROL 「條件類型」]**&#x200B;中，選取&#x200B;**[!UICONTROL 「城市」]**。
1. 輸入條件名稱，例如， **[!UICONTROL SF咖啡店]**.
1. 在右側窗格中，按一下&#x200B;**[!UICONTROL 「目前 POI」]**，然後在下拉式清單中，選取&#x200B;**[!UICONTROL 「舊金山」]**&#x200B;作為您的城市之一。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

### 建立動作

1. 在 **[!UICONTROL 動作]** 區段，按一下 **[!UICONTROL +新增]**.
1. 在 **[!UICONTROL 副檔名]** 下拉式清單，保留預設值 **[!UICONTROL 行動核心]** 已選取選項。
1. 選取動作型別，例如， **[!UICONTROL 傳送回傳]**.

   a.輸入 **[!UICONTROL URL]**，輸入回傳URL以進行Slack，例如， `https://hooks.slack.com/services/`.

   b.若要傳送貼文內文，請選取 **[!UICONTROL 新增貼文內文]** 核取方塊。

   c.輸入 **[!UICONTROL 貼文內文]**，新增貼文內文，例如： `{ "text": "A customer has entered" }`

   c.輸入內容型別，例如 **[!UICONTROL application/json]**.

   d.選取逾時值，例如 **[!UICONTROL 5]**.

1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

### 發佈規則

1. 若要啟用規則，您必須將其發佈。 如需以Experience Platform Launch發佈規則的詳細資訊，請參閱 [發佈](https://docs.adobe.com/content/help/zh-Hant/launch/using/reference/publish/overview.html).

### 超越登入與退出的思維

使用Places Service地理圍欄專案與退出點來觸發Experience Platform Launch中的規則是極其強大的，但您也可以使用位置資料作為觸發其他事件的條件。 例如，您可以讓行動核心追蹤動作事件觸發器準備就緒，可根據應用程式內的特定trackAction呼叫事件觸發。 您可以根據此事件，在執行動作之前，將其他位置條件放置到事件中。 例如，在購買時開啟應用程式內調查 `trackAction` 事件發生，但 **僅限** 如果使用者目前的位置包含特定的Places Service中繼資料。

![建立條件](/help/assets/places-condition.png)
