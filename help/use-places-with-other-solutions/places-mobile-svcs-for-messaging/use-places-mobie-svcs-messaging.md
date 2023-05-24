---
title: 搭配Mobile Services使用Places服務傳送訊息
description: 本節說明如何搭配Mobile Services使用Places Service傳送訊息。
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

使用Mobile Services擴充功能傳送訊息前，請先檢閱下列必要條件：

* 已在Places Service中建立地標。 如需詳細資訊，請參閱 [建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Places Service包含適用於您組織且已改善的全新POI資料庫，該資料庫位於舊版Mobile Services UI之外。 位於行動服務上的POI *管理位置* 頁面導覽僅適用於SDK第4版。

* 以下是 *管理地標* 舊版SDK舊版Mobile Services UI中的POI管理頁面：

   ![舊版UI](/help/assets/legacy-location-v4-ui.png)

* 以下是Places服務UI：

   ![Places服務POI管理UI](/help/assets/places-ui.png)

* ACP SDK已正確設定Places擴充功能。

   這表示資料可在行動應用程式的Experience Platform Launch規則引擎中作為事件和/或條件使用。 如需詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* 熟悉如何在行動應用程式中建立Experience Platform Launch規則並發佈至ACP SDK。

   如需詳細資訊，請參閱 [規則引擎](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch資料元素是從將用於規則引擎的Places擴充功能資料建立。

   如需詳細資訊，請參閱 [資料元素](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## 報告

您必須先完成下列必要條件，才能使用報表：

* 成功將Places服務資料傳送至Adobe Analytics報表套裝。

   如需詳細資訊，請參閱 [搭配Adobe Analytics使用Places Service](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* 熟悉Mobile Services報表。

   如需詳細資訊，請參閱 [報表](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## 報表視覺效果

您可以使用傳送至Adobe Analytics的Places Service資料執行Mobile Service報表。 在以下範例中，當使用者在其中一個POI中有專案時，就會傳送事件。 在此報表中，已在現成可用的使用者報表上新增POI專案事件的篩選器：

![報表視覺效果](/help/assets/report-visualize.png)

Adobe Analytics介面可增加視覺化Places Service資料的靈活性。
