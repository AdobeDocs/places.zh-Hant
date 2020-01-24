---
title: 將Places service與Mobile services搭配使用以傳訊
description: 本節將說明如何搭配Mobile services使用Places Services進行訊息傳送。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Adobe Mobile Services {#places-mobile-services}

在您可以使用Mobile services擴充功能進行傳訊之前，請先檢閱下列必要條件：

* 地標服務已建立興趣點。 For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Places service為您的組織提供新的、改良的POI資料庫，該資料庫位於舊版Mobile Services UI之外。 位於「Mobile Service *Manage Placess* 」頁面導覽的POI僅適用於SDK第4版。

* 以下是舊 *版SDK舊版Mobile Services UI中的「管理位置* POI」管理頁面：

   ![舊版UI](/help/assets/legacy-location-v4-ui.png)

* 以下是Places服務UI:

   ![Places Service POI管理UI](/help/assets/places-ui.png)

* ACP SDK已正確配置Places Service和／或Places Monitor擴展。

   這表示您的行動應用程式的Experience Platform Launch規則引擎中，資料可做為事件和／或條件使用。 如需詳細資訊，請參 [閱「放置擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md) 」或 [「放置監視擴充功能」](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)。

* 熟悉如何在行動應用程式中建立Experience Platform Launch規則並發佈至ACP SDK。

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch資料元素是從將用於規則引擎的Places擴充資料建立。

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## 報告

在使用報告之前，請先完成下列必要條件：

* 成功將Places服務資料傳送至Adobe Analytics報表套裝。

   如需詳細資訊，請 [參閱「搭配Adobe Analytics使用地標服務」](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)。

* 熟悉Mobile services報告。

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## 報告視覺化

您可以使用傳送至Adobe Analytics的Places service資料來執行Mobile Service報表。 在下列範例中，當使用者在其中一個POI中有項目時，會傳送事件。 在此報告中，POI項目事件的篩選器已新增至現成可用的使用者報告：

![報表視覺化](/help/assets/report-visualize.png)

Adobe Analytics介面提供視覺化Places服務資料的額外彈性。

