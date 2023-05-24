---
title: 報告Analytics Workspace中的位置資料
description: 本節提供如何在Analytics Workspace中報告位置資料的相關資訊。
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---

# 報告Analytics Workspace中的位置資料 {#places-in-workspace}

本檔案說明如何在Analytics Workspace中報告位置資料的範例。 每個步驟都將包含高階摘要，以及參考其他檔案頁面所提供的詳細資訊。

## 先決條件

本檔案假設如下：

1. Places擴充功能會在您的應用程式中實作。

   如需有關實作Places擴充功能的詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Adobe Analytics使用者是管理員，有權存取處理規則。

   如需處理規則的詳細資訊，請參閱[處理規則概述](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

1. 在Launch屬性中，已針對您想要的Places服務變數建立資料元素。

   如需Launch中資料元素的詳細資訊，請參閱 [定義資料元素](/help/use-places-launch-workflow/define-data-elements.md).


## 1.建立Launch規則

建立規則，讓SDK在裝置進入POI時傳送資料給Analytics。 建立此類規則的說明請參閱 [傳送POI登入和退出資料至Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) 頁面。

在此範例中，規則的動作已為Analytics請求定義下列值：

* **[!UICONTROL 動作]** 提供下列值： **[!UICONTROL 地標專案]**.

* 內容資料索引鍵 **[!UICONTROL poi.name]** 設為資料元素的值 **[!UICONTROL {%%POI名稱%%}]**.

![&quot;設定動作&quot;](/help/assets/pt-setAction.png)

## 2.建立Analytics變數

若要對應內容資料（在步驟1傳送），必須先為Analytics報表套裝建立變數。 如需在Analytics中建立變數的詳細資訊，請參閱 [轉換變數(eVar)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

在此範例中，轉換變數 **[!UICONTROL Evar2]**，已建立且已命名 **[!UICONTROL 地標POI名稱]**. 您必須針對要在報告中公開的每個位置變數，建立其他變數。

![&quot;建立analytics變數&quot;](/help/assets/aa-evar.png)

## 3.建立處理規則

需要將內容資料（步驟1）對應至Analytics變數（步驟2）。 如需建立處理規則的詳細資訊，請參閱 [處理規則概觀](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules.html).

在此範例中，已建立處理規則來對應內容資料值 **[!UICONTROL poi.name]** 到 **[!UICONTROL 地標POI名稱(eVar2)]**. 需要為已建立的每個位置變數建立其他處理規則。

![&quot;建立處理規則&quot;](/help/assets/aa-processing-rule.png)

## 4.在工作區中產生報表

此步驟顯示Analytics Workspace中的基本報表，用以檢視在步驟1-3中收集的資料。 如需如何使用Analytics Workspace的詳細資訊，請參閱 [Analytics工作區概觀](https://docs.adobe.com/content/help/zh-Hant/analytics/analyze/analysis-workspace/analysis-workspace-features.html).

在此範例中，報表有下列設定：

* 量度 —  **[!UICONTROL 發生次數]**

* Dimension- **[!UICONTROL 動作名稱]**

   * 依Dimension劃分 —  **[!UICONTROL 地標POI名稱]**

![&quot;在工作區中建立報告&quot;](/help/assets/aa-workspace.png)
