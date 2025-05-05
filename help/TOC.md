---
audience: end-user
user-guide-title: Places Service 指南
user-guide-description: Places Service 是地理位置服務，可讓具備位置感知功能的行動應用程式了解位置內容。
feature: Places
source-git-commit: 9f2c6fee6e0d6d075b662cc0b6cbee49cf05ee55
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 18%

---


# Places Service {#using}

+ [Places Service概觀](home.md)
+ [發行說明](release-notes.md)
+ [快速入門](getting-started.md)
+ [取得Places Service的存取權](places-gain-access.md)
+ Places服務UI {#poi-mgmt-ui}
   + [Places Service UI總覽](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [建立POI](poi-mgmt-ui/create-a-poi-ui.md)
   + [管理先前建立的POI](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [搭配POI使用中繼資料的策略](poi-mgmt-ui/metadata-with-pois.md)
   + [大量上傳POI](poi-mgmt-ui/bulk-upload-pois.md)
   + [管理多個程式庫](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ Web服務API {#web-service-api}
   + [網站服務API總覽](web-service-api/places-web-services.md)
   + [整合必要條件](web-service-api/adobe-i-o-integration.md)
   + API使用量{#api-usage}
      + [API使用概述](web-service-api/api-usage/api-usage-overview.md)
      + [標題和引數](web-service-api/api-usage/headers-and-parameters.md)
      + 管理資料庫{#manage-libraries}
         + [管理程式庫概觀](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [建立程式庫](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [讀取程式庫](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [更新程式庫](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [刪除程式庫](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [讀取組織中的所有程式庫](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [在程式庫上設定排名](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [取得資料庫排名](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + 管理地標 {#manage-pois}
         + [管理POI概覽](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [建立POI](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [讀取POI](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [更新POI](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [刪除POI](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [讀取資料庫中的所有POI](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [讀取您組織中的所有POI](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + 批次API {#batch-apis}
            + [批次API總覽](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [建立多個POI](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [更新多個POI](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [刪除多個POI](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [查詢API](web-service-api/api-usage/query-apis.md)
+ 行動SDK的擴充功能 {#places-ext-aep-sdks}
   + [Places延伸模組](places-ext-aep-sdks/places-extension/places-extension.md)
+ [將Places Service與您自己的監控解決方案搭配使用](using-your-own-monitor.md)
+ [不使用作用中區域監視的Places服務](use-places-without-active-monitoring.md)
+ 使用Places Service做為Experience Platform Launch工作流程的一部分{#use-places-launch-workflow}
   + [使用Places Service做為Experience Platform Launch工作流程的一部分](use-places-launch-workflow/places-launch-workflow.md)
   + [定義資料元素](use-places-launch-workflow/define-data-elements.md)
   + [建立登入與退出規則](use-places-launch-workflow/create-rule-places-property.md)
+ 搭配其他Adobe解決方案使用Places Service{#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [搭配Adobe Analytics使用Places Service](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [傳送POI登入和退出資料至Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [將位置內容新增至Analytics請求](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [報告Analytics Workspace中的位置資料](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [推播通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [應用程式內通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [搭配Adobe Campaign Standard使用Places Service](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [推播通知](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [應用程式內訊息](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [搭配Adobe Target使用Places Service](use-places-with-other-solutions/places-target/places-target.md)
+ 測試與驗證{#places-testing-validation}
   + [測試及驗證Places服務](places-testing-validation/test-validate-places.md)
+ [常見問答](places-faqs.md)
