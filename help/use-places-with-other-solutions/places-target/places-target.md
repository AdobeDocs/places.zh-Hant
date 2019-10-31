---
title: Adobe Target
seo-title: Adobe Target
description: 本節提供如何搭配Adobe Target使用位置服務的相關資訊。
seo-description: '本節提供如何搭配Adobe Target使用位置服務的相關資訊。 '
translation-type: tm+mt
source-git-commit: 84b23934a6e9f9fd61c068693bae3daca24de253

---


# Adobe Target {#places-target}

本檔案假設您已在應用程式中實作「位置」擴充功能。 如果您需要實作Places擴充功能的協助，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在「地標」延伸模組傳送登入和退出的事件後，您可以利用「啟動」中的「規則」，將您的「地標」資料附加至您的Adobe Target SDK事件。 在啟動中選取您想要的屬性後，您可以完成下列工作以建立此類型的規則：

## 1.建立規則

1. 在標籤 **[!UICONTROL Rules]** 上，按一下 **[!UICONTROL Create New Rule]**。

   請記住以下資訊:

   * 如果您沒有此屬性的現有規則，則按鈕會位於畫面中間。
   * 如果您的屬性有規則，則按鈕會位於畫面的右上方。

## 2.選擇事件

1. 為規則指定有意義的名稱，以便在規則清單中輕鬆辨識。

   在此範例中，規則為命名 **[!UICONTROL Attach Places Data to Target Content Requested]**。

2. 在區段 **[!UICONTROL Events]** 下，按一下 **[!UICONTROL Add]**。

3. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Adobe Target]**。

4. 從下拉 **[!UICONTROL Event Type]** 式清單中，選取 **[!UICONTROL Content Requested]**。

5. 按一下 **[!UICONTROL Keep Changes]**。

![新增事件](/help/assets/ad-setEvent_target.png)

## 3.新增條件

>[!IMPORTANT]
>
>如果您要將條件新增至規則，請完成此步驟。 否則，請跳至下 *面的定義動作* 。

在下列範例中，會建立條件，使規則僅針對已啟動應用程式五次以上的使用者觸發。

1. 在區段 **[!UICONTROL Conditions]** 下，按一下 **[!UICONTROL Add]**。

2. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Mobile Core]**。

3. 從下拉 **[!UICONTROL Condition Type]** 式清單中，選取 **[!UICONTROL Launches]**。

4. 在右窗格中，修改下拉式清單和數字控制項，讓條件為「 **[!UICONTROL使用者已啟動超過或等於5次的應用程式」**。

5. 按一下 **[!UICONTROL Keep Changes]**。

![新增事件](/help/assets/ad-setCondition_target.png)

## 4.定義動作

1. 在區段 **[!UICONTROL Actions]** 下，按一下 **[!UICONTROL Add]**。

2. 從下拉 **[!UICONTROL Extension]** 式清單中，選取 **[!UICONTROL Mobile Core]**。

3. 從下拉 **[!UICONTROL Action Type]** 式清單中，選取 **[!UICONTROL Attach Data]**。

4. 在右窗格的欄位中， **[!UICONTROL JSON Payload]** 輸入要新增至此事件的資料。

5. 按一下 **[!UICONTROL Keep Changes]**。

在右窗格中，您可以新增自由格式的JSON裝載，在監聽此事件的副檔名之前，將資料新增至SDK事件。

在下列範例中， `poiCity` 會將值 `poiName` 新增至Target事 **[!UICONTROL mboxparameters]** 件中處理的每個請求。 此事件處理時，SDK會動態決定新索引鍵的值。

>[!TIP
>]
>此JSON裝載會對物件使用特殊記 `request` 號。 在原始事件中， `request` 是一組匿名物件。 使用「附加資料」(Attach Data)將資料附加到陣列中的所有對象時，已知包含陣列的鍵上的符號會導致裝載被應用於該陣列中的所有對象。 `[*]`
>
>對於數 `request[*]` 組中的每個對象，可將符號朗讀為_ `request` for。

![新增事件](/help/assets/ad-setAction_target.png)

## 5.儲存規則並重建您的屬性

完成配置後，請確認您的規則看起來與以下映像類似：

![已完成規則](/help/assets/ad-ruleComplete_target.png)

1. 按一下&#x200B;**[!UICONTROL Save]**

2. 重建您的Launch屬性，並將它部署至正確的環境。
