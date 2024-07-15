---
title: 大量上傳POI
description: 本節提供如何大量上傳POI的相關資訊。
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# 大量上傳POI {#bulk-upload-pois}

Places服務中的&#x200B;**匯入POI**&#x200B;按鈕可用來使用CSV檔案大量上傳新的POI。 範例試算表範本可供您顯示需要哪些資料欄，以及如何新增選用的自訂中繼資料。

![大量匯入畫面](/help/assets/Bulk-import.png)

請觀看這段影片，瞭解大量匯入和大量編輯的程式：

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Places服務大量匯入和編輯POI](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python API指令碼

已建立一組Python指令碼，以簡化使用Web服務API將.csv檔案中的POI批次匯入POI資料庫的程式。 可以從這個開放原始碼[Git存放庫](https://github.com/adobe/places-scripts)下載這些指令碼。

在執行這些指令碼之前，若要存取網站服務API，請參閱[整合總覽與必要條件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*使用者存取的必要條件*。

以下是有關指令碼的一些資訊：

>[!TIP]
>
>此資訊也包含在[Git存放庫](https://github.com/adobe/places-scripts)的Readme檔案中。

## CSV 檔案

範例.csv檔案`places_sample.csv`是此封裝的一部分，並包含必要的標頭和範例資料列。 這些標題全部為小寫，且與Places資料庫中使用的保留中繼資料索引鍵相對應。 您新增至.csv檔案的欄會新增至POI資料庫，其位於每個POI的個別中繼資料區段中，做為索引鍵/值組，而標頭值則做為索引鍵。

以下是您需要使用的欄和值的清單：

* `lib_id`

  從POI資料庫取得的有效資料庫ID。

* `type`

  點是目前唯一的有效值。

* `longitude`

  介於–180到180之間的值。

* `latitude`

  介於–85到85之間的值。

* `radius`

  介於10到20,000之間的值。

### 欄值

Places服務UI會使用下列各欄的值：

* 顏色，用來作為圖釘的顏色，代表Places服務UI地圖中POI的位置。
   * 有效值為「」、#3E76D0、#AA99E8、#DC2ABA、#FC685B、#FC962E、#F6C436、#BECE5D、#61B56B和#3DC8DE以及「」。
   * 如果值保留為空白，Places服務UI會使用藍色作為預設顏色。

     值分別對應至藍色(#3E76D0)、紫色(#AA99E8)、fuschia (#DC2ABA)、橘色(#FC685B)、淺橙色(#FC962E)、黃色(#F6C436)、淺綠色(#BECE5D)、綠色(#61B56B)和淺藍色(#3DC8DE)。

* 圖示，用來當作圖釘上的圖示，代表Places服務UI地圖上POI的位置。

   * 有效值包括「」、商店、旅館、汽車、飛機、火車、船、體育場、遊樂園、錨點、燒杯、鈴、出價、書、盒子、公事包、瀏覽、筆刷、建築物、電腦、相機、時鐘、教育、手電筒、追蹤、遊戲、女性、男性、禮物、錘子、心、家、鑰匙、啟動、燈泡、信箱、錢、圖釘、促銷、綵帶、購物車、星星、目標、茶壺、thumbDown、thumbUp、陷阱、獎盃、扳手。

     圖示值會依照其顯示順序如下圖所示：

     UI中的![圖示](/help/assets/UI_icons.png)

   * 如果值保留為空白，UI會使用星形作為預設圖示。

* 未提及的欄可以保留空白。

## 執行指令碼

1. 從[Git存放庫](https://github.com/adobe/places-scripts)下載檔案到您的本機目錄。
1. 在文字編輯器中，開啟`config.py`檔案並完成下列工作：

   a.將下列變數值編輯為字串：

   * `csv_file_path`

     這是您`.csv`檔案的路徑。

   * `access_code`

     這是您呼叫Adobe IMS時取得的存取碼。 如需有關如何取得此存取碼的資訊，請參閱[整合總覽與必要條件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*使用者存取的必要條件*。

   * `org_id`

     要將POI匯入其中的Experience CloudorgID。 如需有關如何取得組織ID的資訊，請參閱[整合總覽與必要條件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*使用者存取的必要條件*。

   * `api_key`

     這是從您的Adobe I/OPlaces整合取得的Places REST API金鑰。 如需如何取得API金鑰的詳細資訊，請參閱[整合總覽與必要條件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*使用者存取的必要條件*。

   b.儲存您的變更。

1. 在終端機視窗中，導覽至`…/places-scripts/import/`目錄。
1. 輸入`python ./places_import.py`並按&#x200B;**[!UICONTROL enter]** (**[!UICONTROL return]**)鍵。


## 預先匯入CSV檢查

指令碼一開始會完成對.csv檔案的下列檢查：

* 是否已指定`.csv`檔案。
* 檔案路徑是否有效。
* 是否包含保留的中繼資料標題。

  保留的中繼資料標題為lib_id、名稱、說明、型別、經度、緯度、半徑、國家/地區、州、城市、街道、類別、圖示和顏色。

  >[!TIP]
  >
  >標頭皆為小寫，可依任何順序列出。

* 驗證CSV檔案區段中指定之欄的值。

如果發現錯誤，指令碼會列印出錯誤並中止。 如果未發現錯誤，指令碼會嘗試以1000的批次匯入POI。 如果已成功匯入批次，指令碼會報告狀態代碼200。 如果批次未成功匯入，則會報告錯誤。

## 單元測試

單元測試位於`tests.py`檔案中，應在每個提取請求之前執行，且應全部通過。 應使用新程式碼新增其他測試。 若要執行測試，請導覽至`…/places-scripts/import/`目錄，然後在終端機中輸入`python ./places_import.py`。
