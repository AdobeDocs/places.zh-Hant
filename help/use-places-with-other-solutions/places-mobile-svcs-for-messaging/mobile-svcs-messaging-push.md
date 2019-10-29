---
title: 推送訊息
seo-title: 推送訊息
description: 本節將說明如何搭配推播訊息使用「地標」。
seo-description: 本節將說明如何搭配推播訊息使用「地標」。
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# 推播通知(#places-push-messaging)

推播通知：AMS可讓您傳送推播通知給Adobe Analytics區段。 「位置服務」可讓您依據推播訊息與POI的歷史互動來劃分其對象。 例如，您可以傳送訊息給過去30天內曾在您其中一家商店的使用者。

開始之前，請確定您已完成下列工作：

* Adobe Analytics已處理位置服務資料。

   這表示您的行動應用程式已成功將位置服務資料傳送至報表套裝，且該資料可供分段。

* 已設定Mobile services中的推播通知頻道。

   如需詳細資訊，請參閱[建立推送訊息](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)。

* 熟悉如何傳送推播通知至Mobile services中的Analytics區段。

   * 如需詳細資訊，請參閱[建立推送訊息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)。

## 傳送通知

在「建 **[!UICONTROL Audience]** 立推播通知 *」工作流程的標籤中* ，您可以透過下列其中一種方式建立此訊息的對象：

* 選取先前建立的Adobe Analytics區段。

* 使用可用的自訂區段參數來建立觀眾。

![設定推播訊息](/help/assets/push-set-up.png)

