---
title: 搭配POI使用中繼資料
description: 本節提供如何搭配POI使用中繼資料的資訊和策略。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# 搭配POI使用中繼資料的策略 {#using-metadata-pois}

在「地點服務」中，當您建立新的POI時，唯一需要的元素是「名稱」、「半徑」、「經度」。 如需建立POI的詳細資訊，請參 [閱建立POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。 但是，如果您只輸入最低資訊，將錯失創造附加價值的機會。

POI中繼資料可以以多種方式使用。 從POI管理的角度來看，新增中繼資料值有助於搜尋或篩選可能數千個POI的清單。 為與POI相關的關鍵屬性建立中繼資料，可在下游工作流程中產生值。 例如，為每家酒店建立POI的連鎖酒店可能會想要包含中繼資料，例如酒店的酒店是否有游泳池、餐廳和酒吧，或者他們是否有健身房設施。 此中繼資料可作為分析中的上下文資料加以包含，也可用於定位選件或傳訊。

## 在Launch中置入服務中繼資料

在Experience Platform Launch中，您可以為每個Places Service中繼資料欄位建立資料元素，這對追蹤或傳訊目的非常重要。

![用於健身設施的資料元](/help/assets/gymfacility.png)

然後，您可以使用Analytics擴充功能建立動作，以建立新點擊，其中包含您想要做為上下文資料的任何中繼資料。

![健身設施的運動](/help/assets/Analytics-gym.png)

## Adobe Campaign中的應用程式內訊息

中繼資料可用作Adobe Campaign Standard中定義之本機通知和應用程式內訊息的篩選。 使用中繼資料做為篩選，可讓您建立與實際位置相關的更相關訊息。

![在ACS中過濾本地通知和應用程式內消息](/help/assets/ACS_gym_metadata.png)