---
title: 常見問題
description: 本主題提供有關一些常見問題的其他資訊。
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
TQID: https://experienceleague.adobe.com/LL9eLMDJaq8ZmeiZxv28QZoqXL1A0QKZ-DvTDUx4Gnw
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 557
ht-degree: 1%

---

# 常見問題

以下是Places Service的部分資訊和常見問答。

## 從v4 SDK中的trackLocation移轉

如果您要從v4 SDK移轉並尋找`trackLocation` API的替代專案，請參閱主題[不使用作用中地區監視的Places服務](use-places-without-active-monitoring.md)。

## 尺寸與可靠性

請務必注意，無論使用Adobe或某些其他服務，行動應用程式地區監視中使用的所有地理柵欄。 作業系統建議建立地理柵欄時要牢記的一些引數。 為了達到最大的可靠性，地理圍欄的半徑應至少為100米。 可以建立較小的地理圍欄，但可能不會產生登入和退出事件，或可能在使用者停止移動一段期間後產生。

此外，可能會根據硬體狀況（例如Wi-Fi已關閉或無法使用），以及根據裝置相對阻礙GPS訊號的位置，來降低精確度和可靠性。 例如，山區、城市設定和室內區域可能會降低iOS和Android作業系統的位置準確度。

## 退出事件如何觸發？

實作的區域監視器應要求附近POI清單。 收到後，區域應該向作業系統註冊每個POI。 作業系統現在負責在裝置超過其中一個受監視區域的邊界（進入或退出）時通知SDK。 SDK只會在作業系統通知SDK該事件已發生時，才會觸發退出事件。 此通知的主要原因是位置資料的時間敏感度。

如果作業系統在裝置離開區域時無法傳遞退出事件，SDK省略退出事件會比較安全。 如果SDK在沒有作業系統觸發事件的情況下製造退出事件，就存在裝置接近POI的時段以外，仍可能妥善處理退出事件的風險。

## POI數量

在Places服務POI管理介面中，客戶可在特定資料庫中新增最多150,000個地標。 如有需要，客戶可定義多個程式庫以區段POI群組。

## 有關位置變更與作用中區域監視的一些注意事項

註冊授權應用程式後，便會立即開始監控地理區域。 不過，請勿期望立即收到事件，因為只有邊界交叉點會產生事件。 特別是，如果註冊時使用者的位置已經在區域內，位置管理員不會自動產生事件。 相反，您的應用程式必須等待使用者越過區域界限，才會產生事件並傳送給代理人。

指定要監視的區域集時，請務必謹慎。 區域是共用的系統資源，而且系統範圍內可用的區域總數是有限的。 因此，核心位置將單一應用程式可同時監控的區域數量限製為20。 若要繞過此限制，請考慮僅註冊使用者鄰近的那些區域。

[檢視Apple開發人員網站的其他資訊] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
