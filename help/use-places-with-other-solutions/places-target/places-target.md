---
title: Adobe Target
description: 本節提供如何搭配Adobe Target使用Places Service的相關資訊。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---

# 搭配Adobe Target使用Places Service {#places-target}

本檔案假設您在應用程式中實作Places擴充功能。 如果您需要實作Places擴充功能的協助，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

在Places擴充功能傳送登入和退出事件後，您可以運用Launch中的規則，將Places服務資料附加至Adobe Target SDK事件。 在Launch中選取所需的屬性後，您可以完成下列工作來建立此型別的規則：

## 1.建立規則

1. 於 **[!UICONTROL 規則]** 標籤，按一下 **[!UICONTROL 建立新規則]**.

   請記住以下資訊：

   * 如果您沒有此屬性的現有規則，則按鈕將位於畫面中間。
   * 如果您的屬性有規則，則按鈕會位於畫面右上方。

## 2.選取事件

1. 為規則提供一個有意義的名稱，以便在規則清單中輕鬆識別。

   在此範例中，規則的名稱為 **[!UICONTROL 將Places服務資料附加至請求的目標內容]**.

1. 在 **[!UICONTROL 事件]** 區段，按一下 **[!UICONTROL 新增]**.
1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL Adobe Target]**.
1. 從 **[!UICONTROL 事件型別]** 下拉式清單，選取 **[!UICONTROL 已要求內容]**.
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

![新增事件](/help/assets/ad-setEvent_target.png)

## 3.新增條件

>[!IMPORTANT]
>
>如果您想要將條件新增至規則，請完成此步驟。 否則，請跳至 *定義動作* 下方的。

在以下範例中，系統會建立條件，讓規則僅針對已啟動應用程式五次或更多次的使用者觸發。

1. 在 **[!UICONTROL 條件]** 區段，按一下 **[!UICONTROL 新增]**.
1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 行動核心]**.
1. 從 **[!UICONTROL 條件型別]** 下拉式清單，選取 **[!UICONTROL 啟動]**.
1. 在右窗格中，修改下拉式清單和數位控制項，讓條件可讀取 **[!UICONTROL 使用者已啟動應用程式超過或等於5次]**.
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

![新增條件](/help/assets/ad-setCondition_target.png)

## 4.定義作業

1. 在 **[!UICONTROL 動作]** 區段，按一下 **[!UICONTROL 新增]**.
1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL 行動核心]**.
1. 從 **[!UICONTROL 動作型別]** 下拉式清單，選取 **[!UICONTROL 附加資料]**.
1. 在右窗格的 **[!UICONTROL JSON裝載]** 欄位中，輸入將新增至此事件的資料。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

在右側窗格中，您可以新增自由格式JSON裝載，此裝載會在監聽此事件的擴充功能聆聽之前，將資料新增至SDK事件。

在以下範例中， `poiCity` 和 `poiName` 值會新增至 **[!UICONTROL mboxparameters]** Target事件中處理的每個要求。 新金鑰的值會在此事件處理時由SDK動態決定。

>[!TIP]
>
>此JSON裝載使用特殊標籤法來 `request` 物件。 在原始事件中， `request` 是匿名物件的陣列。 使用「附加資料」將資料附加至陣列中的所有物件時， `[*]` 在已知包含陣列的索引鍵上加上標籤法，會使裝載套用至該陣列中的所有物件。
>
>表示法 `request[*]` 可大聲朗讀為 _每個物件的 `request` 陣列_.

![定義動作](/help/assets/ad-setAction-target.png)

## 5.儲存規則並重新建置您的屬性

完成設定後，請確認您的規則看起來像以下影像：

![已完成規則](/help/assets/ad-ruleComplete-target.png)

1. 按一下&#x200B;**[!UICONTROL 儲存]**
1. 重新建置Launch屬性，並將其部署至正確的環境。
