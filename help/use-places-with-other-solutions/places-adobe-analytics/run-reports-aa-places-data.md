---
title: 將位置內容新增至Analytics請求
description: 本節提供如何新增位置內容至Analytics請求的相關資訊。
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 1%

---

# 將位置內容新增至Analytics請求 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>本檔案假設您在應用程式中實施了Places服務。 如需實作Places服務的詳細資訊，請參閱[Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

Places Service傳送登入和退出事件後，您可以在Experience Platform Launch中建立規則，並將Places Service資料附加至所有Adobe Analytics事件。 若要建立此型別的規則，請在Launch中選取您的屬性，並完成下列步驟：

## 1.建立規則

1. 在&#x200B;**[!UICONTROL 規則]**&#x200B;標籤上，按一下&#x200B;**[!UICONTROL 建立新規則]**。

   請記住以下資訊：
   * 如果您沒有此屬性的現有規則，**[!UICONTROL 建立新規則]**&#x200B;按鈕將會在畫面中央。
   * 如果您的屬性有規則，**[!UICONTROL 建立新規則]**&#x200B;按鈕將會在畫面的右上角。

## 2.選取事件

1. 為規則提供一個有意義的名稱，以便在規則清單中輕鬆識別。

   在此範例中，規則的名稱為&#x200B;**[!UICONTROL 將Places服務資料附加至Analytics追蹤動作事件]**。

1. 在&#x200B;**[!UICONTROL 事件]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。

1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 行動核心]**。

1. 從&#x200B;**[!UICONTROL 事件型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 追蹤動作]**。

現在您可以決定要納入此規則的觸發器。 在此範例中，觸發器是以所有`TrackAction`呼叫為基礎。 設定事件後，按一下[保留變更]。**&#x200B;**

![&quot;建立事件&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.新增條件

>[!IMPORTANT]
>
>完成此程式，將條件新增至規則。 否則，請跳到下面的&#x200B;*定義動作*&#x200B;區段。

在此範例中，會建立條件，使規則僅針對AT&amp;T客戶觸發。

1. 在&#x200B;**[!UICONTROL 條件]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。

1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 行動核心]**。

1. 從&#x200B;**[!UICONTROL 條件型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 電信業者名稱]**。

1. 在右側視窗中，選取&#x200B;**[!UICONTROL AT&amp;T]**&#x200B;核取方塊。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

![&quot;建立條件&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.定義作業

1. 在&#x200B;**[!UICONTROL 動作]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。

1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 行動核心]**。

1. 從&#x200B;**[!UICONTROL 動作型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 附加資料]**。

1. 在右窗格的&#x200B;**[!UICONTROL JSON裝載]**&#x200B;欄位中，輸入將新增至此事件的資料。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

在右側窗格中，您可以新增自由格式JSON裝載，此裝載會先將資料新增至SDK事件，然後偵聽此事件的擴充功能才能聽到該事件。 在此範例中，某些內容資料會在Analytics擴充功能處理前新增至此事件。 新增的內容資料現在會保留在傳出的Analytics點選上。

在下列範例中，`poi.city`和`poi.name`值已新增至Analytics事件的內容資料。 新金鑰的值在此事件處理時由SDK動態決定。

![&quot;建立動作&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5.儲存規則並重新建置您的屬性

完成設定後，請確認您的規則看起來像下列影像：

![&quot;規則已完成。&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 按一下&#x200B;**[!UICONTROL 儲存]**

1. 重新建置Launch屬性，並將其部署至正確的環境。
