---
title: 傳送POI登入和退出資料至Analytics
description: 本節提供如何將POI登入與退出資料傳送至Analytics的相關資訊。
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# 傳送POI登入和退出資料至Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>本節假設您已在應用程式中實施Places服務。 如需實作Places服務的詳細資訊，請參閱[Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

Places服務傳送登入和退出事件後，您可以在Experience Platform Launch中建立規則，將Places服務資料傳送至Adobe Analytics。 若要建立此型別的規則，請在Launch中選取您的屬性，並完成下列步驟：

## 1.建立規則

1. 在&#x200B;**[!UICONTROL 規則]**&#x200B;標籤上，按一下&#x200B;**[!UICONTROL 建立新規則]**。

   請記住以下資訊：

   * 如果您沒有此屬性的現有規則，**[!UICONTROL 建立新規則]**&#x200B;按鈕將會在畫面中央。
   * 如果您的屬性有規則，**[!UICONTROL 建立新規則]**&#x200B;按鈕將會在畫面的右上角。

## 2.選取事件

1. 為您的規則輸入有意義的名稱。

   如此一來，您就可以在規則清單中輕鬆辨識規則。 在此範例中，規則的名稱為&#x200B;**[!UICONTROL 將資料傳送至Analytics]**。

1. 在&#x200B;**[!UICONTROL 事件]**&#x200B;區段中，按一下&#x200B;**[!UICONTROL 新增]**。

1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL Places服務]**。

1. 從&#x200B;**[!UICONTROL 事件型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 輸入POI]**。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

   ![「選取事件」](/help/assets/pt-selectEvent.png)


## 3.新增條件

>[!IMPORTANT]
>
>完成此步驟，將條件新增至規則。 否則，請跳到下面的&#x200B;*定義動作*。

在此範例中，會建立條件，讓規則只在「目前POI」名稱等於&#x200B;**[!UICONTROL 我的POI]**&#x200B;時觸發。

1. 在&#x200B;**[!UICONTROL 條件]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。

1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL Places服務]**。

1. 從&#x200B;**[!UICONTROL 條件型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 名稱]**。

1. 在右窗格的文字欄位中，輸入&#x200B;**[!UICONTROL 我的POI]**。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

   ![&quot;設定條件&quot;](/help/assets/pt-setCondition.png)


## 4.定義作業

1. 在&#x200B;**[!UICONTROL 動作]**&#x200B;區段下，按一下&#x200B;**[!UICONTROL 新增]**。

1. 從&#x200B;**[!UICONTROL 擴充功能]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL Adobe Analytics]**。

1. 從&#x200B;**[!UICONTROL 動作型別]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 追蹤]**。

1. 在右窗格中，新增您要傳送至Analytics的動作或狀態。

   您也可以選擇將任何其他內容資料新增至此請求。 請記住，您可以使用資料元素，以動態方式從SDK取得此資料。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**。

   在下列範例中，會傳送`TrackAction`呼叫至Analytics，其`poi.name`的其他內容資料等於觸發此專案事件的POI名稱：

   ![「設定動作」](/help/assets/pt-setAction.png)

## 5.儲存規則並重新建置您的屬性

完成設定後，請確認您的規則看起來像下列影像：

![&quot;已建立規則&quot;](/help/assets/pt-ruleComplete.png)

1. 按一下&#x200B;**[!UICONTROL 儲存]**

1. 重新建置Launch屬性，並將其部署至正確的環境。
