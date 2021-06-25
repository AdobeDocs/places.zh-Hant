---
title: Places監視擴展
description: Places Monitor擴充功能可處理與作業系統的互動，以註冊並監視最接近使用者的POI。
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Places監視擴展 {#places-monitor-extension}

Places Monitor擴充功能可處理與作業系統的互動，以註冊並監視最接近使用者的POI。 此擴充功能會擷取需要從Places擴充功能註冊的POI，並將登入和退出通知傳遞至Places擴充功能。 這些通知將在Experience Platform Launch規則中以事件形式提供。

「監視」擴充功能為選用，因為某些客戶可能已經使用作業系統監視地區。 如果是這種情況，請確定您新增Places擴充功能API，以接收來自Places Service資料庫的最接近POI，並傳遞登入與退出事件，以採取適當的動作。

## Places監視器淘汰

2021年8月31日起，Adobe Experience Platform Mobile SDK的Places監視擴充功能將不再使用。 8月31日之後，Places Monitor擴充功能將不會收到更新或支援。

目前使用Places Monitor擴充功能的客戶可繼續使用此擴充功能，但需了解，不會透過Adobe提供其他更新或支援。

Places Monitor擴充功能的淘汰對Places Service擴充功能沒有影響或負面影響，我們將持續支援這些擴充功能及更新。

希望從Places監視器擴充功能過渡到其自己的監視解決方案的客戶，應查閱以下文檔：[將Places服務與您自己的監控解決方案搭配使用](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en)。 本檔案說明如何透過從Google Play在iOS上實作[核心位置服務](https://developer.apple.com/documentation/corelocation)或[位置服務](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary)，與Places服務互動。
