---
title: 推播通知
description: 本節將說明如何搭配推播通知使用Places Service。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# 推播通知

Mobile services可讓您傳送推播通知給Adobe Analytics區段。 在「地標服務」中，您可以使用推送訊息與POI的歷史互動來區隔其對象。 例如，您可以傳送訊息給過去30天內曾在您其中一家商店中的使用者。

開始之前，請確定您已完成下列工作：

* Places service資料已由Adobe Analytics處理。

   這表示您的行動應用程式已成功將Places service資料傳送至報表套裝，且該資料可供分段。

* 已設定Mobile services中的推播通知頻道。

   如需詳細資訊，請參閱[建立推送訊息](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)。

* 瞭解如何傳送推播通知至Mobile services中的Analytics區段。

   如需詳細資訊，請參閱[建立推送訊息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)。

## 傳送通知

在「建 **[!UICONTROL Audience]**立推播通知&#x200B;*」工作流程的標籤上*，您可以透過下列其中一種方式建立此訊息的對象：

* 在下拉 **[!UICONTROL Analytics Segments]**式清單中，選取先前建立的Adobe Analytics區段。

* 在區 **[!UICONTROL Custom Segment]**段中，使用可用的自訂區段參數來建立觀眾。

![設定推播訊息](/help/assets/push-set-up.png)
