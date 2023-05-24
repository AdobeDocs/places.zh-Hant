---
title: 推播通知
description: 本節說明如何搭配推播通知使用Places服務。
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 8%

---

# 推播通知

Mobile Services可讓您將推播通知傳送至Adobe Analytics區段。 在Places Service中，您可以使用推送訊息與您的POI之間的歷史互動，以細分推送訊息的對象。 例如，您可以傳送訊息給過去30天內曾到過您其中一個商店的使用者。

開始之前，請確定您已完成下列工作：

* Adobe Analytics已處理Places服務資料。

   這表示您的行動應用程式已成功將Places服務資料傳送至報表套裝，且資料可用於分段。

* 行動服務中的推播通知頻道已設定。

   如需詳細資訊，請參閱[建立推送訊息](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)。

* 瞭解如何在Mobile Services中將推播通知傳送至Analytics區段。

   如需詳細資訊，請參閱[建立推送訊息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)。

## 傳送通知

於 **[!UICONTROL 對象]** 的標籤 *建立推播通知* 工作流程中，您可以透過下列其中一種方式建立此訊息的對象：

* 在 **[!UICONTROL Analytics區段]** 從下拉式清單中，選取先前建立的Adobe Analytics區段。

* 在 **[!UICONTROL 自訂區段]** 區段，使用可用的自訂區段引數來建立對象。

![設定推送訊息](/help/assets/push-set-up.png)
