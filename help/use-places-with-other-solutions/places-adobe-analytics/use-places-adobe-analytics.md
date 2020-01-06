---
title: 傳送POI登入與退出資料至Analytics
description: 本節提供如何傳送POI登入與退出資料至Analytics的相關資訊。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# 傳送POI登入與退出資料至Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>本節假設您已在應用程式中實作「地點」。 如需實作「地標」的詳細資訊，請參閱「地 [標」擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places傳送進入和退出事件後，您可以在Experience Platform Launch中建立規則，將Places資料傳送至Adobe Analytics。 若要建立此類型的規則，請在啟動中選取您的屬性，然後完成下列步驟：

## 1.建立規則

1. 在標籤 **[!UICONTROL Rules]**上，按一下**[!UICONTROL Create New Rule]**。

   請記住以下資訊:

   * 如果您沒有此屬性的現有規則， **[!UICONTROL Create New Rule]**按鈕就會位於畫面中間。
   * 如果您的屬性有規則， **[!UICONTROL Create New Rule]**則按鈕會位於畫面右上方。

## 2.選擇事件

1. 為規則輸入有意義的名稱。

   如此，規則就可在您的規則清單中輕鬆辨識。 在此範例中，規則為命名 **[!UICONTROL Send Data to Analytics]**。

1. In the **[!UICONTROL Events]**section, click**[!UICONTROL Add]**.

1. 從下拉 **[!UICONTROL Extension]**式清單中，選取**[!UICONTROL Places]**。

1. 從下拉 **[!UICONTROL Event Type]**式清單中，選取**[!UICONTROL Enter POI]**。

1. 按一下 **[!UICONTROL Keep Changes]**。

   ![&quot;選擇事件&quot;](/help/assets/pt-selectEvent.png)


## 3.新增條件

>[!IMPORTANT]
>
>完成此步驟，將條件新增至規則。 否則，請跳至 *下方定義動作* 。

在此範例中，會建立條件，僅在目前POI的名稱等於時，才會觸發規則 **[!UICONTROL My POI]**。

1. 在區段 **[!UICONTROL Conditions]**下，按一下**[!UICONTROL Add]**。

1. 從下拉 **[!UICONTROL Extension]**式清單中，選取**[!UICONTROL Places]**。

1. 從下拉 **[!UICONTROL Condition Type]**式清單中，選取**[!UICONTROL Name]**。

1. 在右窗格中的文本欄位中，輸入 **[!UICONTROL My POI]**。

1. 按一下 **[!UICONTROL Keep Changes]**。

   ![&quot;設定條件&quot;](/help/assets/pt-setCondition.png)


## 4.定義動作

1. 在區段 **[!UICONTROL Actions]**下，按一下**[!UICONTROL Add]**。

1. 從下拉 **[!UICONTROL Extension]**式清單中，選取**[!UICONTROL Adobe Analytics]**。

1. 從下拉 **[!UICONTROL Action Type]**式清單中，選取**[!UICONTROL Track]**。

1. 在右窗格中，新增您要傳送至Analytics的動作或狀態。

   您也可以選擇新增任何其他內容資料至此請求。 請記住，您可以使用資料元素從SDK動態取得此資料。

1. 按一下 **[!UICONTROL Keep Changes]**。

   在下列範例中， `TrackAction` 會傳送呼叫至Analytics，其他內容資料等 `poi.name` 於觸發此登入事件之POI的名稱：

   ![&quot;設定動作&quot;](/help/assets/pt-setAction.png)

## 5.儲存規則並重建您的屬性

完成配置後，請確認您的規則看起來與以下映像類似：

![&quot;規則已建立&quot;](/help/assets/pt-ruleComplete.png)

1. 按一下 **[!UICONTROL Save]**

1. 重建您的Launch屬性，並將它部署至正確的環境。
