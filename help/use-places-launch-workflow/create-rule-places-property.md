---
title: 為Places服務屬性建立規則
description: Places SDK可追蹤目前位置、監控目前位置周圍已設定的POI，以及追蹤這些POI的登入和退出事件。
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 15%

---

# 建立登入與退出規則 {#create-entry-exit-rules}

在行動應用程式中安裝Places擴充功能和地區監控解決方案後，您就可以在Adobe Experience Platform Launch中建立受觸發或條件限制的位置資料（包括位置登入和退出事件）的規則。

## 規則

您可以設定由事件、條件和動作組成的規則。 每個規則皆由下列部分組成：

* 一或多個事件
* （選用）條件
* 一或多個動作

### Places服務事件

Places Service提供下列事件，供您執行規則：

* **輸入POI**，此會在客戶進入您設定的POI時由Places SDK觸發。
* **退出POI**，此會在客戶退出您設定的POI時，由Places SDK觸發。

### Places服務條件

條件會定義與事件相關聯的資料，或該執行個體上擴充功能的共用狀態，必須符合的條件，才能執行動作。 例如，您可以設定條件，只對舊金山市的咖啡店進入觸發動作。

Places SDK會維護下列狀態：

* 目前的POI，是指客戶目前所在的POI。
* 上次退出POI，是指客戶最近退出的POI。
* 上次輸入的POI，這是指客戶最近輸入的POI。

每個POI都包含下列資料元素：

* ID
* 名稱
* 經緯度
* 半徑
* 中繼資料，例如城市、國家、州、類別

### 動作

動作會定義應用程式在回應觸發事件的符合規則條件時所將執行的操作。 例如，當客戶進入POI時，您可以設定歡迎訊息以顯示在其行動裝置上。

## 建立規則：範例

>[!CAUTION]
>
>此範例假設您已建立美國所有咖啡店的 POI 資料庫。如需建立POI和程式庫的詳細資訊，請參閱 [建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md) 和 *建立程式庫* in [管理多個程式庫](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

以下程式是如何建立規則的範例，當您進入舊金山的咖啡店時，會將貼文傳回Slack。

事件、條件和動作的定義方式如下：

* **事件**:放置登入事件。
* **條件**：**「目前 POI」**&#x200B;的城市是舊金山
* **動作**:發送回傳以Slack客戶輸入的咖啡店名稱。

### 先決條件

建立規則之前，您必須在Adobe Experience Platform Launch中建立資料元素。 資料元素會自動在回傳訊息中填入有關POI的必要資訊。

若要在Experience Platform Launch中建立資料元素：

1. 按一下 **資料元素** 標籤。
1. 按一下&#x200B;**新增資料元素**.
1. 輸入名稱，例如 **當前咖啡店名稱**.
1. 在 **擴充功能** 下拉清單，選擇 **Places — 測試版**.
1. 在&#x200B;**「資料元素」**&#x200B;中，選取&#x200B;**「城市」**。
1. 在右窗格中，選取 **目前POI**.
1. 按一下「**儲存**」。

### 在Places服務的Experience Platform Launch中建立規則

![建立規則](/help/assets/placesrule.png)

1. 在 Experience 平台 Launch 中，按一下 **[!UICONTROL 「規則」]**&#x200B;標籤。
1. 按一下&#x200B;**[!UICONTROL 新增規則]**.
1. 輸入規則的名稱，例如 **[!UICONTROL 在SF中跟蹤咖啡店入口]**.

### 建立事件

1. 在「事件」區段中，按一下 **[!UICONTROL +新增]**. 事件決定您要在何時觸發規則。
1. 在 **[!UICONTROL 擴充功能]** 下拉清單，選擇 **[!UICONTROL Places — 測試版]**.
1. 在&#x200B;**[!UICONTROL 「事件類型」]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 「輸入 POI」]**。
1. 在&#x200B;**[!UICONTROL 「名稱」]**&#x200B;中，輸入事件的名稱，例如 **[!UICONTROL Entering a coffee shop]**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

### 建立條件

1. 在「條件」區段中，按一下 **[!UICONTROL +添加]**. 條件決定要採取行動必須符合哪些標準。
1. 在&#x200B;**[!UICONTROL 「邏輯類型」]**&#x200B;中，選取「規則」，以允許在滿足條件時執行動作。
1. 在 **[!UICONTROL 擴充功能]** 下拉清單，選擇 **[!UICONTROL Places — 測試版]**.
1. 在&#x200B;**[!UICONTROL 「條件類型」]**&#x200B;中，選取&#x200B;**[!UICONTROL 「城市」]**。
1. 輸入條件名稱，例如 **[!UICONTROL SF的咖啡店]**.
1. 在右側窗格中，按一下&#x200B;**[!UICONTROL 「目前 POI」]**，然後在下拉式清單中，選取&#x200B;**[!UICONTROL 「舊金山」]**&#x200B;作為您的城市之一。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

### 建立動作

1. 在 **[!UICONTROL 動作]** ，按一下 **[!UICONTROL +新增]**.
1. 在 **[!UICONTROL 擴充功能]** 下拉式清單，保留預設值 **[!UICONTROL 行動核心]** 選項。
1. 選取動作類型，例如 **[!UICONTROL 傳送回傳]**.

   a.在 **[!UICONTROL URL]**，輸入Slack的回傳URL，例如 `https://hooks.slack.com/services/`.

   b.若要傳送貼文內文，請選取 **[!UICONTROL 新增貼文內文]** 框。

   c.輸入 **[!UICONTROL 貼文內文]**，新增貼文內文，例如： `{ "text": "A customer has entered" }`

   c.輸入內容類型，例如 **[!UICONTROL application/json]**.

   d.選取逾時值，例如 **[!UICONTROL 5]**.

1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

### 發佈規則

1. 若要啟用規則，您必須發佈它。 如需在Experience Platform Launch中發佈規則的詳細資訊，請參閱 [發佈](https://docs.adobe.com/content/help/zh-Hant/launch/using/reference/publish/overview.html).

### 超越進出

在Experience Platform Launch中使用Places Service的地理圍欄項目和退出來觸發規則功能強大得令人難以置信，但您也可以使用位置資料作為其他事件觸發的條件。 例如，您可以讓行動核心追蹤動作事件觸發器準備好根據應用程式內的特定trackAction呼叫事件觸發。 根據此事件，您可以在執行動作之前將其他位置條件放入事件。 例如，在購買時開啟應用程式內調查 `trackAction` 事件發生，但 **僅限** 如果使用者的目前位置包含特定的Places服務中繼資料。

![建立條件](/help/assets/places-condition.png)
