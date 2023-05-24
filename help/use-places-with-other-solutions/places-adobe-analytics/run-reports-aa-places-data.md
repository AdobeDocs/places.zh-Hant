---
title: 將位置內容新增至Analytics請求
description: 本節提供如何新增位置內容至Analytics請求的相關資訊。
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---

# 將位置內容新增至Analytics請求 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>本檔案假設您已在應用程式中實施Places服務。 如需實作Places Service的詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Places服務傳送登入和退出事件後，您可以在Experience Platform Launch中建立規則，並將Places服務資料附加至所有Adobe Analytics事件。 若要建立此型別的規則，請在Launch中選取您的屬性，並完成下列步驟：

## 1.建立規則

1. 於 **[!UICONTROL 規則]** 標籤，按一下 **[!UICONTROL 建立新規則]**.

   請記住以下資訊：
   * 如果您沒有此屬性的現有規則， **[!UICONTROL 建立新規則]** 按鈕將位於畫面中間。
   * 如果您的屬性有規則， **[!UICONTROL 建立新規則]** 按鈕將位於畫面的右上方。

## 2.選取事件

1. 為規則提供一個有意義的名稱，以便在規則清單中輕鬆識別。

   在此範例中，規則的名稱為 **[!UICONTROL 將Places服務資料附加至Analytics追蹤動作事件]**.

1. 在 **[!UICONTROL 事件]** 區段，按一下 **[!UICONTROL 新增]**.

1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 行動核心]**.

1. 從 **[!UICONTROL 事件型別]** 下拉式清單，選取 **[!UICONTROL 追蹤動作]**.

現在您可以決定要納入此規則的觸發器。 在此範例中，觸發器是根據 `TrackAction` 呼叫。 設定事件後，按一下 **[!UICONTROL 保留變更]**.

![&quot;建立事件&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.新增條件

>[!IMPORTANT]
>
>完成此程式，將條件新增至規則。 否則，請跳至 *定義動作* 區段底下。

在此範例中，會建立條件，使規則僅針對AT&amp;T客戶觸發。

1. 在 **[!UICONTROL 條件]** 區段，按一下 **[!UICONTROL 新增]**.

1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 行動核心]**.

1. 從 **[!UICONTROL 條件型別]** 下拉式清單，選取 **[!UICONTROL 電信業者名稱]**.

1. 在右側的視窗中，選取 **[!UICONTROL AT&amp;T]** 核取方塊。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

![&quot;建立條件&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.定義作業

1. 在 **[!UICONTROL 動作]** 區段，按一下 **[!UICONTROL 新增]**.

1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 行動核心]**.

1. 從 **[!UICONTROL 動作型別]** 下拉式清單，選取 **[!UICONTROL 附加資料]**.

1. 在右窗格的 **[!UICONTROL JSON裝載]** 欄位中，輸入將新增至此事件的資料。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

在右側窗格中，您可以新增自由格式JSON裝載，此裝載會在聆聽此事件的擴充功能聽到事件之前，將資料新增至SDK事件。 在此範例中，某些內容資料會在Analytics擴充功能處理此事件之前新增至此事件。 新增的內容資料現在會位於傳出的Analytics點選上。

在以下範例中， `poi.city` 和 `poi.name` 值會新增至Analytics事件的內容資料。 新金鑰的值會在此事件處理時由SDK動態決定。

![&quot;建立動作&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5.儲存規則並重新建置您的屬性

完成設定後，請確認您的規則看起來像以下影像：

![「規則已完成。」](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 按一下&#x200B;**[!UICONTROL 儲存]**

1. 重新建置Launch屬性，並將其部署至正確的環境。
