---
title: 新增位置內容至Analytics請求
description: 本節提供如何新增位置內容至Analytics請求的相關資訊。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# 新增位置內容至Analytics請求 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>本檔案假設您已在應用程式中實作Adobe Places。 如需實作Adobe Places的詳細資訊，請參閱「地 [標擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)」。

在Places傳送進入和退出事件後，您可以在Experience Platform Launch中建立規則，並將您的Places資料附加至所有Adobe Analytics事件。 若要建立此類型的規則，請在啟動中選取您的屬性，然後完成下列步驟：

## 1.建立規則

1. 在標籤 **[!UICONTROL Rules]** 上，按一下 **[!UICONTROL Create New Rule]**。

   請記住以下資訊:
   * 如果您沒有此屬性的現有規則， **[!UICONTROL Create New Rule]** 按鈕就會位於畫面中間。
   * 如果您的屬性有規則， **[!UICONTROL Create New Rule]** 則按鈕會位於畫面右上方。

## 2.選擇事件

1. 為規則指定有意義的名稱，以便在規則清單中輕鬆辨識。

   在此範例中，規則為命名 **[!UICONTROL Attach Places Data to Analytics Track Action Events]**。

1. 在區段 **[!UICONTROL Events]** 下，按一下 **[!UICONTROL Add]**。

1. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Mobile Core]**。

1. 從下拉 **[!UICONTROL Event Type]** 式清單中，選取 **[!UICONTROL Track Action]**。

現在您可以決定要納入此規則的觸發器。 在此範例中，觸發器是以所有呼叫為 `TrackAction` 基礎。 設定事件後，按一下 **[!UICONTROL Keep Changes]**。

!["建立事件"](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.新增條件

>[!IMPORTANT]
>
>完成此步驟，將條件新增至規則。 否則，請跳至下 *面的「定義動作* 」區段。

在此範例中，會建立條件，讓規則僅針對AT&amp;T客戶觸發。

1. 在區段 **[!UICONTROL Conditions]** 下，按一下 **[!UICONTROL Add]**。

1. 從下拉 **[!UICONTROL Extension]** 式清單中，選取「 **[!UICONTORL 行動核心」]**。

1. 從下拉 **[!UICONTROL Condition Type]** 式清單中，選取 **[!UICONTROL Carrier Name]**。

1. 在右側的窗口中，選中複選框 **[!UICONTROL AT&T]** 。

1. 按一下 **[!UICONTROL Keep Changes]**。

!["建立條件"](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.定義動作

1. 在區段 **[!UICONTROL Actions]** 下，按一下 **[!UICONTROL Add]**。

1. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Mobile Core]**。

1. 從下拉 **[!UICONTROL Action Type]** 式清單中，選取 **[!UICONTROL Attach Data]**。

1. 在右窗格的欄位中， **[!UICONTROL JSON Payload]** 輸入要新增至此事件的資料。

1. 按一下 **[!UICONTROL Keep Changes]**。

在右窗格中，您可以新增自由格式的JSON裝載，將資料新增至SDK事件，然後監聽此事件的副檔名才能聽到該事件。 在此範例中，有些上下文資料會在Analytics擴充功能處理前新增至此事件。 新增的上下文資料現在會出現在傳出的Analytics點擊上。

在下列範例中， `poi.city` 值 `poi.name` 會新增至Analytics事件的上下文資料。 當此事件處理時，新索引鍵的值會由SDK動態決定。

![「建立動作」](/help/assets/ad-setAction_use-analytics-data.png)

## 5.儲存規則並重建您的屬性

完成配置後，請確認您的規則看起來與以下映像類似：

!["規則已完成。"](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 按一下&#x200B;**[!UICONTROL Save]**

1. 重建您的Launch屬性，並將它部署至正確的環境。
