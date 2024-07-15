---
title: Adobe Target
description: 本節提供如何搭配Adobe Target使用Places Service的相關資訊。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 1%

---

# 搭配Adobe Target使用Places Service {#places-target}

本檔案假設您已在應用程式中實施Places擴充功能。 若您需要實作Places擴充功能的協助，請參閱[Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places擴充功能傳送進入和退出的事件後，您可以運用Launch中的規則，將Places服務資料附加至Adobe Target SDK事件。 在Launch中選取所需的屬性後，您可以完成下列工作來建立此型別的規則：

## 1.建立規則

1. 在&#x200B;**[!UICONTROL 規則]**&#x200B;標籤上，按一下&#x200B;**[!UICONTROL 建立新規則]**。

   請記住以下資訊：

   * 如果您沒有此屬性的現有規則，則按鈕會位於畫面中央。
   * 如果您的屬性有規則，按鈕將會位於畫面右上方。

## 2.選取事件

1. 為規則提供一個有意義的名稱，以便在規則清單中輕鬆識別。

   在此範例中，規則的名稱為&#x200B;**[!UICONTROL 將Places服務資料附加至請求的目標內容]**。

1. 在&#x200B;**[!UICONTROL 事件]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。
1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL Adobe Target]**。
1. 從&#x200B;**[!UICONTROL 事件型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 要求的內容]**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

![新增事件](/help/assets/ad-setEvent_target.png)

## 3.新增條件

>[!IMPORTANT]
>
>如果您想要將條件新增至規則，請完成此步驟。 否則，請跳到下面的&#x200B;*定義動作*。

在以下範例中，已建立條件，讓規則僅針對已啟動應用程式五次或更多次的使用者觸發。

1. 在&#x200B;**[!UICONTROL 條件]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。
1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 行動核心]**。
1. 從&#x200B;**[!UICONTROL 條件型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 啟動]**。
1. 在右窗格中，修改下拉式清單和數位控制項，讓條件顯示&#x200B;**[!UICONTROL 使用者已啟動應用程式超過或等於5次]**。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

![新增條件](/help/assets/ad-setCondition_target.png)

## 4.定義作業

1. 在&#x200B;**[!UICONTROL 動作]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。
1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 行動核心]**。
1. 從&#x200B;**[!UICONTROL 動作型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 附加資料]**。
1. 在右窗格的&#x200B;**[!UICONTROL JSON裝載]**&#x200B;欄位中，輸入將新增至此事件的資料。
1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

在右窗格中，您可以新增自由格式JSON裝載，該裝載會在SDK事件中新增資料，然後擴充功能就會接聽此事件。

在下列範例中，針對在Target事件中處理的每個要求，`poiCity`與`poiName`值已新增至&#x200B;**[!UICONTROL mboxparameters]**。 新金鑰的值在此事件處理時由SDK動態決定。

>[!TIP]
>
>此JSON裝載對`request`物件使用特殊標籤法。 在原始事件中，`request`是匿名物件的陣列。 當使用附加資料將資料附加到陣列中的所有物件時，已知包含陣列的索引鍵上的`[*]`標籤法會導致裝載套用到該陣列中的所有物件。
>
>對於`request`陣列&#x200B;_中的每個物件，`request[*]`的標籤可以朗讀為_。

![定義動作](/help/assets/ad-setAction-target.png)

## 5.儲存規則並重新建置您的屬性

完成設定後，請確認您的規則看起來像下列影像：

![已完成規則](/help/assets/ad-ruleComplete-target.png)

1. 按一下&#x200B;**[!UICONTROL 儲存]**
1. 重新建置Launch屬性，並將其部署至正確的環境。
