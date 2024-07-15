---
title: 搭配使用POI中繼資料
description: 本節提供如何搭配POI使用中繼資料的相關資訊和策略。
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# 搭配POI使用中繼資料的策略 {#using-metadata-pois}

在Places Service中，當您建立新的POI時，只需要名稱、半徑、緯度和經度元素。 如需建立POI的詳細資訊，請參閱[建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。 但是，如果您只輸入最小資訊，則會錯過建立額外值的機會。

POI中繼資料可以透過多種方式使用。 從POI管理的角度來看，新增中繼資料值有助於搜尋或篩選可能數千個POI的清單。 為與POI相關的主要屬性建立中繼資料，可能會在下游工作流程中產生值。 例如，為每個屬性建立POI的連鎖飯店可能想要包含中繼資料，例如飯店屬性是否具有游泳池、餐廳和酒吧，或它們是否具有健身房設施。 此中繼資料可作為Analytics中的內容資料納入，也可用於目標選件或傳訊。

## 在Launch中放置服務中繼資料

在Experience Platform Launch中，您可以針對追蹤或傳訊用途上重要的每個Places Service中繼資料欄位，建立資料元素。

健身房設施的![資料元素](/help/assets/gymfacility.png)

您可以使用Analytics擴充功能建立動作，以建立新點選，其中包含您想當作內容資料的任何中繼資料。

健身設施的![動作](/help/assets/Analytics-gym.png)

## Adobe Campaign中的應用程式內傳訊

中繼資料可作為Adobe Campaign Standard中定義的本機通知和應用程式內訊息的篩選器。 使用中繼資料作為篩選條件，可讓您建立與實際位置更相關的訊息。

![在ACS中篩選本機通知和應用程式內訊息](/help/assets/ACS_gym_metadata.png)
