---
title: 為「地標」屬性建立規則
seo-title: 為「地標」屬性建立規則
description: 'Places SDK會追蹤目前位置、監視目前位置周圍已設定的POI，並追蹤這些POI的登入與退出事件。 '
seo-description: 'Places SDK會追蹤目前位置、監視目前位置周圍已設定的POI，並追蹤這些POI的登入與退出事件。 '
translation-type: tm+mt
source-git-commit: 84b23934a6e9f9fd61c068693bae3daca24de253

---


# 建立登入與退出規則 {#create-entry-exit-rules}

在行動應用程式中安裝Places and Places Monitor擴充功能後，您就可以在Adobe Experience Platform Launch中建立規則，以觸發或限制位置資料，包括位置進入和退出事件。

## 規則

您可以設定由事件、條件和動作組成的規則。 每個規則都由下列內容組成：

* 一個或多個事件
* （可選）條件
* 一個或多個動作

### 放置事件

「地標」提供下列事件，您可在其中執行規則：

* **輸入POI**，當您的客戶輸入您設定的POI時，Places SDK會觸發此POI。
* **退出POI**，當客戶退出您設定的POI時，Places SDK會觸發此POI。

### 地點條件

條件定義與事件關聯的資料或該例項中擴充功能的共用狀態，必須符合的條件，才能執行動作。 例如，您可以設定條件，只在舊金山市觸發進入咖啡店的動作。

Places SDK會維持下列狀態：

* 目前的POI，指您的客戶目前所在的POI。
* 上次退出POI，這是指客戶退出的最近POI。
* 上次輸入的POI，是指您的客戶最近輸入的POI。

每個POI都包含下列資料元素：

* ID
* 名稱:
* 經緯度
* 半徑
* 中繼資料，例如城市、國家、州、類別

### 動作

動作會定義應用程式將針對符合引發事件規則條件而執行的動作。 例如，當您的客戶進入您的POI時，您可以設定歡迎訊息以顯示在其行動裝置上。

## 建立規則：範例

>[!CAUTION]
>
>此範例假設您已建立美國所有咖啡店的POI資料庫。 如需有關建立POI和程式庫的詳細資訊，請參 [閱「管理多個程式庫」中的「建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md)*和建立程式庫* 」 [一節](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html)。

以下程式是如何建立規則的範例，當您進入舊金山的咖啡店時，會將貼文傳回Slack。

事件、條件和動作的定義方式如下：

* **事件**:放置參加項目事件。
* **條件**:目前的 **POI城市** ，是舊金山
* **動作**:將回傳給Slack您客戶輸入的咖啡店名稱。

### 先決條件

在建立規則之前，您必須先在Adobe Experience Platform Launch中建立資料元素。 資料元素會自動在回傳訊息中填入有關您POI的必要資訊。

若要在Experience Platform Launch中建立資料元素：

1. 按一下「 **資料元素** 」標籤。
2. Click **Add Data Element**.
3. 鍵入名稱，例如，「當 **前咖啡店名稱」**。
4. 在「擴 **充功能** 」下拉式清單中，選 **取「位置——測試版」**。
5. 在「 **資料元素**」中，選 **取「城市」**。
6. 在右窗格中，選擇「當 **前POI」**。
7. 按一下&#x200B;**「儲存」**。

### 在Experience Platform Launch for Places中建立規則

![建立規則](/help/assets/placesrule.png)

1. 在Experience Platform Launch中，按一下標 **[!UICONTROL Rules]** 簽。
2. 按一下 **[!UICONTROL Add Rule]**。
3. 鍵入規則的名稱，例如 **[!UICONTROL Track entry for coffee shop in SF]**。

### 建立事件

1. 在「事件」區段中，按一下 **[!UICONTROL + Add]**。 事件會決定您要何時觸發規則。
2. 在下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Places – Beta]**。
3. 在下拉 **[!UICONTROL Event Type]** 式清單中，選取 **[!UICONTROL Enter POI]**。
4. 在 **[!UICONTROL Name]**&#x200B;中，輸入事件的名稱，例如 **[!UICONTROL Entering a coffee shop]**。
5. 按一下 **[!UICONTROL Keep Changes]**。

### 建立條件

1. 在「條件」區段中，按一下 **[!UICONTROL +Add]**。 條件決定了要採取的動作必須符合哪些標準。
2. 在中， **[!UICONTROL Logic Type]**&#x200B;選擇「常規」(Regular)，該選項允許在滿足條件時執行操作。
3. 在下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Places – Beta]**。
4. 在中 **[!UICONTROL Condition Type]**，選擇 **[!UICONTROL City]**。
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. 在右窗格中，按一 **[!UICONTROL Current POI]**&#x200B;下，然後在下拉式清單中，選 **[!UICONTROL San Francisco]** 取其中一個城市。
7. 按一下 **[!UICONTROL Keep Changes]**。

### 建立動作

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL + Add]**.
2. 在下拉 **[!UICONTROL Extension]** 式清單中，保留預設選 **[!UICONTROL Mobile Core]** 項的選取。
3. 選擇操作類型，例如 **[!UICONTROL Send Postback]**。

   a.在 **[!UICONTROL URL]**&#x200B;中，鍵入Slack的回傳URL，例如 `https://hooks.slack.com/services/`。

   b.若要傳送貼文內文，請選取核取 **[!UICONTROL Add Post Body]** 方塊。

   c.在中 **[!UICONTROL Post Body]**&#x200B;新增貼文內文，例如： `{ "text": "A customer has entered" }`

   c.例如，鍵入內容類型 **[!UICONTROL application/json]**。

   d.選擇超時值，例如 **[!UICONTROL 5]**。

4. 按一下 **[!UICONTROL Keep Changes]**。

### 發佈規則

1. 若要啟用規則，您必須發佈規則。 如需有關在Experience Platform Launch中發佈規則的詳細資訊，請參閱發 [布](https://docs.adobelaunch.com/launch-reference/publishing)。

### 從進出出出發思考

在Experience Platform Launch中使用位置服務地理柵欄登入和退出來觸發規則功能非常強大，但您也可以使用位置資料作為其他事件觸發的條件。 例如，您可以根據應用程式內的特定trackAction呼叫事件，讓「行動核心追蹤動作」事件觸發器準備好觸發。 根據此事件，您可以在執行動作之前，將其他位置條件置入事件。 例如，當發生購買事件時開啟應用程式內調查，但 `trackAction` 僅在使用者目 **前位置包含特定** 「位置服務」中繼資料時才開啟。

![建立條件](/help/assets/places-condition.png)