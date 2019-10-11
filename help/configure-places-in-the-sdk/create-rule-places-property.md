---
title: 為「地標」屬性建立規則
seo-title: 為「地標」屬性建立規則
description: 'Places SDK會追蹤目前位置、監視目前位置周圍已設定的POI，並追蹤這些POI的登入與退出事件。 '
seo-description: 'Places SDK會追蹤目前位置、監視目前位置周圍已設定的POI，並追蹤這些POI的登入與退出事件。 '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 為「地標」屬性建立規則 {#creating-rule-places-property}

「位置服務SDK」會追蹤目前位置、監視目前位置周圍所設定的POI，並追蹤這些POI的登入和退出事件。

## 規則

您可以設定由事件、條件和動作組成的規則。 每個規則都由下列內容組成：

* 一個或多個事件
* （可選）條件
* 一個或多個動作

### 事件

「地標」提供下列事件，您可在其中執行規則：

* **[!UICONTROL Enter POI]**，而此SDK是由客戶輸入您所設定的POI時的Places SDK觸發。
* **[!UICONTROL Exit POI]**，而Places SDK會在您的客戶退出您設定的POI時觸發。

### 條件

條件定義與事件關聯的資料或該例項中擴充功能的共用狀態，必須符合的條件，才能執行動作。 例如，您可以設定條件，只在舊金山市觸發進入咖啡店的動作。

位置服務SDK會維持下列狀態：

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
>此範例假設您已建立美國所有咖啡店的POI資料庫。 如需建立POI和資料庫的詳細資訊，請 [參閱建立POI](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/managing-pois-in-the-places-ui#create-a-poi)[和建立資料庫](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/manage-libraries#create-a-library)。

以下程式是如何建立規則的範例，當您進入舊金山的咖啡店時，會將貼文傳回Slack。

事件、條件和動作的定義方式如下：

* **事件**:位置服務登入事件。
* **條件**:目前的 **POI城市** ，是舊金山
* **動作**:將回傳給Slack您客戶輸入的咖啡店名稱。

### 先決條件

在建立規則之前，您必須先在Experience Platform Launch中建立資料元素。 資料元素會自動在回傳訊息中填入有關您POI的必要資訊。

若要在Experience Platform Launch中建立資料元素：

1. Click the **[!UICONTROL Data Elements]** tab.
2. 按一下 **[!UICONTROL Add Data Element]**。
3. Type a name, for example, **[!UICONTROL Current coffee shop name]**.
4. 在下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Places – Beta]**。
5. 在中 **[!UICONTROL Data Element]**，選擇 **[!UICONTROL City]**。
6. 在右窗格中，選擇「當 **前POI」**。
7. 按一下 **[!UICONTROL Save]**。

### 在Experience Platform Launch for Location service中建立規則

![](//help/assets/create-a-rule.png)

1. 在Experience Platform Launch中，按一下標 **[!UICONTROL Rules]** 簽。
2. Click **Add Rule**.
3. 輸入規則的名稱，例如，在SF中 **追蹤咖啡店的項目**。

### 建立事件

1. 在「事件」區段中，按一下 **[!UICONTROL + Add]**。 事件會決定您要何時觸發規則。
2. 在下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Places – Beta]**。
3. 在下拉 **[!UICONTROL Event Type]** 式清單中，選取 **[!UICONTROL Enter POI]**。
4. 在 **[!UICONTROL Name]**&#x200B;中，輸入事件的名稱，例如 **[!UICONTROL Entering a coffee shop]**。
5. 按一下 **[!UICONTROL Keep Changes]**。

### 建立條件

1. 在「條件」區段中，按一下 **[!UICONTROL +Add]**。 條件決定了要採取的動作必須符合哪些標準。
2. 在中， **[!UICONTROL Logic Type]**&#x200B;選擇「常規」(Regular)，該選項允許在滿足條件時執行操作。
3. 在「擴 **充功能** 」下拉式清單中，選取 **[!UICONTROL Places – Beta]**。
4. 在中 **[!UICONTROL Condition Type]**，選擇 **[!UICONTROL City]**。
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. 在右窗格中，按一 **[!UICONTROL Current POI]**&#x200B;下，然後在下拉式清單中，選 **[!UICONTROL San Francisco]** 取其中一個城市。
7. 按一下 **[!UICONTROL Keep Changes]**。

### 建立動作

1. 在區段 **[!UICONTROL Actions]** 中，按一下 **[!UICONTRO+新增]**。
2. 在「延 **[!UICONTRO 伸功能]** 」下拉式清單中，保留預設的 **[!UICONTRO 「行動核心]** 」選項。
3. 選取動作類型，例如「傳 **[!UICONTRO 送回傳」]**。

   a.在 **[!UICONTROL URL]**&#x200B;中，鍵入Slack的回傳URL，例如 `https://hooks.slack.com/services/`。

   b.若要傳送貼文內文，請選取「新 **[!UICONTRO 增貼文內文]** 」核取方塊。

   c.在 **[!UICONTRO 貼文內文]**，新增貼文內文，例如： `{ "text": "A customer has entered" }`

   c.輸入內容類型，例如 **[!UICONTRO application/json]**。

   d.選取逾時值，例如 **5**。

4. Click **[!UICONTRO Keep Changes]**.

### 發佈規則

1. 若要啟用規則，您必須發佈規則。 如需有關在Experience Platform Launch中發佈規則的詳細資訊，請參閱發 [布](https://docs.adobelaunch.com/launch-reference/publishing)。