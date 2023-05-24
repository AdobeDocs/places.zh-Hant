---
title: 傳送POI登入和退出資料至Analytics
description: 本節提供如何將POI登入和退出資料傳送至Analytics的相關資訊。
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---

# 傳送POI登入和退出資料至Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>本節假設您已在應用程式中實施Places服務。 如需實作Places Service的詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Places服務傳送登入和退出事件後，您可以在Experience Platform Launch中建立規則，將Places服務資料傳送至Adobe Analytics。 若要建立此型別的規則，請在Launch中選取您的屬性，並完成下列步驟：

## 1.建立規則

1. 於 **[!UICONTROL 規則]** 標籤，按一下 **[!UICONTROL 建立新規則]**.

   請記住以下資訊：

   * 如果您沒有此屬性的現有規則， **[!UICONTROL 建立新規則]** 按鈕將位於畫面中間。
   * 如果您的屬性有規則， **[!UICONTROL 建立新規則]** 按鈕將位於畫面的右上方。

## 2.選取事件

1. 為您的規則輸入有意義的名稱。

   如此一來，規則便可在規則清單中輕鬆識別。 在此範例中，規則的名稱為 **[!UICONTROL 將資料傳送至Analytics]**.

1. 在 **[!UICONTROL 事件]** 區段，按一下 **[!UICONTROL 新增]**.

1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL Places Service]**.

1. 從 **[!UICONTROL 事件型別]** 下拉式清單，選取 **[!UICONTROL 輸入POI]**.

1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

   ![&quot;選取事件&quot;](/help/assets/pt-selectEvent.png)


## 3.新增條件

>[!IMPORTANT]
>
>完成此步驟以將條件新增至規則。 否則，請跳至 *定義動作* 下方的。

在此範例中，會建立條件，使規則只在「目前POI」名稱等於時觸發 **[!UICONTROL 我的POI]**.

1. 在 **[!UICONTROL 條件]** 區段，按一下 **[!UICONTROL 新增]**.

1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL Places Service]**.

1. 從 **[!UICONTROL 條件型別]** 下拉式清單，選取 **[!UICONTROL 名稱]**.

1. 在右窗格的文字欄位中，輸入 **[!UICONTROL 我的POI]**.

1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

   ![&quot;設定條件&quot;](/help/assets/pt-setCondition.png)


## 4.定義作業

1. 在 **[!UICONTROL 動作]** 區段，按一下 **[!UICONTROL 新增]**.

1. 從 **[!UICONTROL 副檔名]** 下拉式清單，選取 **[!UICONTROL Adobe Analytics]**.

1. 從 **[!UICONTROL 動作型別]** 下拉式清單，選取 **[!UICONTROL 曲目]**.

1. 在右窗格中，新增您要傳送至Analytics的動作或狀態。

   您也可以選擇將任何其他內容資料新增至此請求。 請記住，您可以使用資料元素，以動態方式從SDK取得此資料。

1. 按一下&#x200B;**[!UICONTROL 保留變更]**.

   在以下範例中， `TrackAction` 呼叫會傳送至Analytics，並包含其他內容資料 `poi.name` 等於觸發此專案事件的POI名稱：

   ![&quot;設定動作&quot;](/help/assets/pt-setAction.png)

## 5.儲存規則並重新建置您的屬性

完成設定後，請確認您的規則看起來像以下影像：

![&quot;規則已建立&quot;](/help/assets/pt-ruleComplete.png)

1. 按一下&#x200B;**[!UICONTROL 儲存]**

1. 重新建置Launch屬性，並將其部署至正確的環境。
