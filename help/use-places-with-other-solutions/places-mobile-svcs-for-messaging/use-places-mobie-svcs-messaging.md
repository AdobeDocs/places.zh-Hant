---
title: 將Places服務與Mobile Services搭配使用以傳送訊息
description: 本節說明如何搭配Mobile Services使用Places Service進行傳訊。
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

請先檢閱下列必要條件，再使用Mobile Services擴充功能進行傳訊：

* 地標已在Places服務中建立。 如需詳細資訊，請參閱 [建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Places Service包含您組織的全新和改良POI資料庫，其存在於舊版Mobile Services UI之外。 位於Mobile Service上的POI *管理位置* 頁面導覽僅適用於SDK第4版。

* 以下是 *管理位置* 舊版SDK舊版Mobile Services使用者介面中的POI管理頁面：

   ![舊版UI](/help/assets/legacy-location-v4-ui.png)

* 以下是Places Service UI:

   ![Places服務POI管理UI](/help/assets/places-ui.png)

* ACP SDK已正確配置Places擴展。

   這表示資料可在行動應用程式的Experience Platform Launch規則引擎中，以事件和/或條件的形式提供。 如需詳細資訊，請參閱 [Places擴充功能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* 熟悉如何在您的行動應用程式中建立和發佈Experience Platform Launch規則至ACP SDK。

   如需詳細資訊，請參閱 [規則引擎](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch資料元素是從將用於規則引擎的Places擴充功能資料建立。

   如需詳細資訊，請參閱 [資料元素](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## 報告

請先完成下列必要條件，再使用報表：

* 成功將Places服務資料傳送至Adobe Analytics報表套裝。

   如需詳細資訊，請參閱 [搭配使用Places服務Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* 熟悉Mobile Services報表。

   如需詳細資訊，請參閱 [報表](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## 報表視覺效果

您可以使用傳送至Adobe Analytics的Places Service資料來執行Mobile Service報表。 在下列範例中，當使用者在其中一個POI中有項目時，會傳送事件。 在此報表中，已將POI項目事件的篩選器新增至現成可用的使用者報表中：

![報表視覺效果](/help/assets/report-visualize.png)

在Adobe Analytics介面中提供視覺化Places Service資料的額外彈性。
