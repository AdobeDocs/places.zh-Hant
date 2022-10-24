---
title: 常見問答
description: 本主題提供一些常見問題的其他資訊。
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# 常見問答

以下是有關Places Service的一些資訊和常見問題。

## 在v4 SDK中從trackLocation移轉

如果您正從v4 SDK移轉，且正在尋找取代 `trackLocation` API，請參閱主題 [不使用活動區域監視的Places服務](use-places-without-active-monitoring.md).

## 大小和可靠性

請務必注意，無論使用Adobe或其他服務，行動應用程式在區域監控中所使用的所有地理柵欄，皆須如此。 作業系統建議在建立地理柵欄時應記住一些參數。 為達到最高可靠性，地理柵欄的半徑應至少為100米。 可以建立較小的地理柵欄，但登入和退出事件可能不會產生，或可能會在使用者停止移動一段時間後產生。

此外，可以基於諸如被關閉或不可用的wi-fi等硬體條件以及基於與妨礙GPS信號有關的設備的位置，來降低精確度和可靠性。 例如，山區、城市設定和室內區域可能會降低iOS和Android作業系統的位置準確度。

## 退出事件如何觸發？

實作的地區監視器應要求附近POI的清單。 收到後，應將每個POI的地區註冊到作業系統。 作業系統現在負責在裝置跨越其中一個監控區域的邊界（進入或退出）時通知SDK。 作業系統通知SDK事件已發生時，SDK才會觸發退出事件。 此通知的主要原因是位置資料的時間敏感性。

如果裝置離開地區時作業系統無法傳送退出事件，SDK僅忽略退出事件較安全。 如果SDK製作退出事件，而未觸發作業系統所觸發的事件，則有可能在裝置接近POI的時段之外，順利處理退出事件。

## POI數量

在Places Service POI管理介面中，客戶在特定資料庫中最多可新增15萬個地標。 客戶可視需要定義多個資料庫，以劃分POI的群組。

## 關於位置變更和作用中區域監控的一些附註

註冊授權應用程式後，就會立即開始監控地理區域。 但是，不要期望立即收到事件，因為只有邊界交叉點才會生成事件。 尤其是，如果使用者的位置在註冊時已位於地區內，位置管理員不會自動產生事件。 反之，您的應用程式必須等待使用者越過地區界限，才會產生事件並傳送至委派。

指定要監視的區域集時，請謹慎。 區域是共用的系統資源，系統範圍內可用的區域總數有限。 因此，核心位置限制為單一應用程式可同時監控的地區數量上限為20。 要繞過此限制，請考慮僅在用戶附近註冊這些區域。

[請參閱Apple開發人員網站的其他資訊] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
