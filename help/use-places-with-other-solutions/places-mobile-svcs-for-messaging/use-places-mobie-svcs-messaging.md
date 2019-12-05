---
title: 搭配Mobile services使用地標傳訊
description: 本節將說明如何搭配Mobile services使用Places進行傳訊。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Adobe Mobile Services {#places-mobile-services}

在您可以使用Mobile services擴充功能進行傳訊之前，請先檢閱下列必要條件：

* 地點已在「位置服務」中建立。 如有需要，請參閱檔案。 （連結至建立POI）注意：「位置服務」為您的組織提供全新和改良的興趣點資料庫，其存在於舊式AMS介面之外。 在AMS的「管理地標」導覽中找到的任何POI僅適用於SDK第4版。
   * 以下是舊版SDK AMS中舊版的Places POI管理介面：

      ![舊版UI](/help/assets/legacy-location-v4-ui.png)

   * 以下是位置服務POI管理介面：

      ![位置服務POI管理UI](/help/assets/places-ui.png)

* ACP SDK已正確配置Places和／或Places Monitor擴展。 這表示您的行動應用程式的「啟動規則」引擎中，資料可做為事件和／或條件使用。 視需要參閱檔案。 (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* 熟悉如何在行動應用程式中建立Launch規則並發佈至ACP SDK。 視需要參閱檔案。 (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* 「啟動資料元素」是從將用於「規則」的Places SDK擴充功能資料建立。 請參閱檔案(https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)

## 報告

在使用報告之前，請先完成下列必要條件：

* 成功將位置服務資料傳送至Adobe Analytics報表套裝。 如有需要，請造訪Adobe Analytics檔案（Steve的檔案連結）。
* 熟悉AMS報告。 如有需要，請造訪檔案(https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)

## 報告視覺化

您可以使用傳送至Adobe Analytics的位置服務資料來執行AMS報表。 例如，我已在使用者在其中一個POI中有項目時傳送事件。 在此報表中，我已在現成可用的使用者報表上新增POI項目事件的篩選器：

![報表視覺化](/help/assets/report-visualize.png)

Adobe Analytics介面提供視覺化位置服務資料的額外彈性。

