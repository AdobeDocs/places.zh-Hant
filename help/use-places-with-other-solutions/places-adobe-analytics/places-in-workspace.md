---
title: Analytics工作區中位置資料的報告
description: 本節提供如何報告Analytics工作區中位置資料的相關資訊。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Analytics工作區中位置資料的報告 {#places-in-workspace}

本檔案顯示如何在Analytics工作區中報告位置資料的範例。 每個步驟都包含高階摘要，並參考其他檔案頁面提供詳細資訊。

## 必要條件

本檔案假設：

1. Adobe Places擴充功能已實作在您的應用程式中。 如需實作Adobe Places的詳細資訊，請參閱「地 [標擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md)」。

1. Adobe Analytics使用者是管理員，可存取處理規則。 如需處理規則的詳細資訊，請參閱[處理規則概述](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

1. 在「啟動」屬性中，已針對所要的位置服務變數建立資料元素。 如需Launch中資料元素的詳細資訊，請參 [閱定義資料元素](/help/use-places-launch-workflow/define-data-elements.md)。


## 1.建立啟動規則

建立規則，當裝置輸入POI時，SDK會傳送資料至Analytics。 「傳送POI登入和退出資料至Analytics」頁面 [上會說明建立此類規則](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) 。

在此範例中，規則的動作具有為Analytics請求定義的下列值：

* **[!UICONTROL Action]**的值**[!UICONTROL Places Entry]**。

* 上下文資料 **[!UICONTROL poi.name]**索引鍵設為資料元素的值**[!UICONTROL {%%POI Name%%}]**。

![&quot;設定動作&quot;](/help/assets/pt-setAction.png)

## 2.建立Analytics變數

為了對應上下文資料（在步驟1中傳送），必須先為Analytics報表套裝建立變數。 如需在Analytics中建立變數的詳細資訊，請參 [閱轉換變數\(eVars\)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html)。

在此範例中，已建立並 **[!UICONTROL Evar2]**命名轉換變數**[!UICONTROL Places POI Name]**。 您需要為每個要在報表中公開的位置變數建立其他變數。

![「建立分析變數」](/help/assets/aa-evar.png)

## 3.建立處理規則

此步驟需要將上下文資料（步驟1）對應至Analytics變數（步驟2）。 For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

在此範例中，已建立處理規則，將上下文資料值對應至 **[!UICONTROL poi.name]**中**[!UICONTROL Places POI Name \(eVar2\)]**。 需要為每個建立的位置變數建立其他處理規則。

![&quot;建立處理規則&quot;](/help/assets/aa-processing-rule.png)

## 4.在工作區中產生報表

此步驟顯示Analytics工作區中的基本報表，以檢視步驟1-3中收集的資料。 如需如何使用Analytics工作區的詳細資訊，請參閱 [Analytics工作區概述](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html)。

在此範例中，報表具有下列設定：

* 量度 - **[!UICONTROL Occurrences]**

* 維度 - **[!UICONTROL Action Name]**

   * 依維度劃分- **[!UICONTROL Places POI Name]**

![「在工作區中建立報表」](/help/assets/aa-workspace.png)
