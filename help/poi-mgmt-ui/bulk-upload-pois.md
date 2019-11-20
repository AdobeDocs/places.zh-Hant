---
title: 大量上傳POI
seo-title: 大量上傳POI
description: 本節提供如何大量上傳POI的相關資訊。
seo-description: 本節提供如何大量上傳POI的相關資訊。
translation-type: tm+mt
source-git-commit: 3e2bf2ce011f9770209af08bd0abf0b16f84fbc0

---


# 大量上傳POI {#bulk-upload-pois}

已建立一組Python指令碼，以利使用Web服務API，將POI從。csv檔案批次匯入POI資料庫。 這些指令碼可從此開放原始碼 [git repo下載](https://github.com/adobe/places-scripts)。

在您執行這些指令碼之前，若要存取web service API，請參閱「整合概 *述」和「必要條件」中的*[使用者存取必要條件](/help/web-service-api/adobe-i-o-integration.md)。

以下是有關指令碼的一些資訊：

>[!TIP]
>
>這些資訊也包含在git repo的讀我檔案 [中](https://github.com/adobe/places-scripts)。

## CSV檔案

範例。csv檔案 `places_sample.csv`是此套件的一部分，包含必要的標題和一列範例資料。 這些標題都是小寫，並對應於Places資料庫中使用的保留中繼資料索引鍵。 您新增至。csv檔案的欄會以每個POI的索引鍵／值配對形式，新增至POI資料庫的個別中繼資料區段，而標題值則用作索引鍵。

以下是您需要使用的欄和值的清單：

* `lib_id`

   從POI資料庫取得的有效程式庫ID。

* `type`

   Point目前是唯一有效值。

* `longitude`

   介於-180和180之間的值。

* `latitude`

   介於-85和85之間的值。

* `radius`

   值介於10到20,000之間。

### 欄值

「位置服務」UI中使用下列欄的值：

* color，此顏色用作PIN的顏色，代表POI在位置服務UI映射中的位置。
   * 有效值為「」、#3E76D0、#AA99E8、#DC2ABA、#FC685B、#FC962E、#F6C436、#BECE5D、#61B56b和#3DC8DE和""。
   * 如果值保留為空白，則定位服務UI會使用藍色作為預設顏色。

      這些值對應藍色(#3E76D0)、紫色(#AA99E8)、fuschia(#DC2ABA)、橘色(#FC685B)、淡橙(#FC962E)、黃色(#F6C436)、淡綠色(#BECE5D)、綠色(#61B56B)和淺藍色(#3DC8DE)。

* 表徵圖，此表徵圖用作PIN上的表徵圖，該表徵圖代表POI在位置服務UI映射上的位置

   * 有效值為""、商店、旅館、汽車、火車、船、體育場、娛樂園、錨、燒杯、鐘、投標、書、箱、公事包、瀏覽、筆刷、建築、計算器、相機、鐘、教育、手電筒、追隨者、遊戲、男性、禮物、錘、心、家、鑰匙、啟動、燈泡、郵箱、銷、促銷、緞帶、購物車、星目標，茶壺，拇指向下，拇指向上，陷阱，獎杯，扳手。

      圖示值依其在下圖中的顯示順序列出：

      ![圖示](/help/assets/UI_icons.png)

   * 如果值保留為空白，UI會使用星號作為預設圖示。

* 未提及的欄可留空。

## 運行指令碼

1. 從Git repo下載 [檔案](https://github.com/adobe/places-scripts) ，到您的本機目錄。
1. 在文字編輯器中，開啟 `config.py` 檔案並完成下列工作：

   a.將下列變數值編輯為字串：

   * `csv_file_path`

      這是您檔案的路 `.csv` 徑。

   * `access_code`

      這是您從呼叫Adobe IMS所取得的存取代碼。 如需如何取得此存取程式碼的詳細資訊，請參閱「整合概 *述」中的「使用者存取的必要條件* 」 [和必要條件](/help/web-service-api/adobe-i-o-integration.md)。

   * `org_id`

      要匯入POI的Experience cloud組織ID。 如需如何取得組織ID的詳細資訊，請參閱「整合概 *述」中的使用者存取*[必要條件和必要條件](/help/web-service-api/adobe-i-o-integration.md)。

   * `api_key`

      這是您從Adobe I/O Places整合取得的Places REST API金鑰。 如需如何取得API金鑰的詳細資訊，請參閱「整合概 *述」中的使用者存取*[必要條件和必要條件](/help/web-service-api/adobe-i-o-integration.md)。
   b.儲存您的變更。

1. 在終端窗口中，導航到該 `…/places-scripts/import/` 目錄。
1. 輸 `python ./places_import.py` 入並按 **[!UICONTROL enter]** (**[!UICONTROL return]**)鍵。


## 預先匯入CSV檢查

指令碼最初會完成。csv檔案的下列檢查：

* 是否指 `.csv` 定檔案。
* 檔案路徑是否有效。
* 是否包含保留的中繼資料標題。

   保留的中繼資料標題為lib_id、名稱、說明、類型、經度、緯度、半徑、國家、州、城市、街道、類別、圖示和顏色。

   >[!TIP]
   >
   >標題皆為小寫，可依任何順序列出。

* 驗證在CSV檔案部分中指定的列的值。

如果發現錯誤，指令碼將打印出錯誤並中止。 如果未找到錯誤，指令碼將嘗試以1000批導入POI。 如果批次成功導入，指令碼將報告狀態代碼200。 如果批未成功導入，則報告錯誤。

## 設備測試

設備測試位於文 `tests.py` 件中，應在每個提取請求之前運行，並且應全部通過。 應新增其他測試與新程式碼。 若要執行測試，請導覽至目 `…/places-scripts/import/` 錄，然後在 `python ./places_import.py` 終端機中輸入。
