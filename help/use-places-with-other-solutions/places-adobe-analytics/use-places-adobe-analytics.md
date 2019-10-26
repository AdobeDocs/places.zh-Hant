---
title: 傳送地點資料至Adobe Analytics
seo-title: 傳送地點資料至Adobe Analytics
description: 本節提供如何將「地標」資料傳送至Analytics的相關資訊。
seo-description: '本節提供如何將「地標」資料傳送至Analytics的相關資訊。 '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# 傳送地點資料至Adobe Analytics {#places-data-analytics}


（Steve影片的預留位置）。

>[!IMPORTANT]
>
>本檔案假設您的應用程式中已實作「位置」。 如需實作「地標」的詳細資訊，請參閱「地 [標擴充功能」](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places傳送進入和退出事件後，您可以在Experience Platform Launch中建立規則，將Places資料傳送至Adobe Analytics。 若要建立此類型的規則，請在啟動中選取您的屬性，然後完成下列步驟：

## 1.建立規則

1. 在標籤 **[!UICONTROL Rules]** 上，按一下 **[!UICONTROL Create New Rule]**。

   請記住以下資訊:

   * 如果您沒有此屬性的現有規則，則按鈕會位於畫面中間。
   * 如果您的屬性有規則，則按鈕會位於畫面的右上方。

## 2.選擇事件

1. 為規則指定有意義的名稱，以便在規則清單中輕鬆辨識。 在此範例中，規則名為「傳送 **資料至Analytics」**。

2. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Places]**。

4. 從下拉 **[!UICONTROL Event Type]** 式清單中，選取 **[!UICONTROL Enter POI]**。

5. 按一下 **[!UICONTROL Keep Changes]**。

   !["選擇事件"](/help/assets/pt-selectEvent.png)


## 3.新增條件

>[!IMPORTANT]
>
>如果您要將條件新增至規則，請完成此步驟。 否則，請跳至 *下方定義動作* 。


在此範例中，會建立條件，僅在目前POI的名稱等於時，才會觸發規則 **[!UICONTROL My POI]**。

1. 在區段 **[!UICONTROL Conditions]** 下，按一下 **[!UICONTROL Add]**。

2. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Places]**。

3. 從下拉 **[!UICONTROL Condition Type]** 式清單中，選取 **[!UICONTROL Name]**。

4. 在右側的窗口中，在文本欄位中輸入 **[!UICONTROL My POI]**。

5. 按一下 **[!UICONTROL Keep Changes]**。

   !["設定條件"](/help/assets/ad-setCondition.png)


## 4.定義動作

1. 在區段 **[!UICONTROL Actions]** 下，按一下 **[!UICONTROL Add]**。

2. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Adobe Analytics]**。

3. 從下拉 **[!UICONTROL Action Type]** 式清單中，選取 **[!UICONTROL Track]**。

4. 在右窗格中，新增您要傳送至Analytics的動作或狀態。 您也可以選擇新增任何其他內容資料至此請求。 請記住，您可以使用資料元素從SDK動態取得此資料。

5. 按一下 **[!UICONTROL Keep Changes]**。

在下列範例中， `TrackAction` 會傳送呼叫至Analytics，其他 **poi.name** 的上下文資料等於觸發此參加項目事件的POI名稱：

!["設定動作"](/help/assets/pt-setAction.png)

## 5.儲存規則並重建您的屬性

完成配置後，請確認您的規則看起來與以下映像類似：

!["規則已建立"](/help/assets/pt-ruleComplete.png)


1. 按一下&#x200B;**[!UICONTROL Save]**

2. 重建您的Launch屬性，並將它部署至正確的環境。

