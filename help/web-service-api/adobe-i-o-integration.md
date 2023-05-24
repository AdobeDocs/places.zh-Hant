---
title: Adobe I/O整合概述
description: 有關建立Adobe I/O整合的資訊。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---

# 整合概述和先決條件 {#integration-prereqs}

此資訊會示範如何建立Adobe I/O和Places服務整合。

## 使用者存取的必要條件

向貴組織的系統管理員確認下列工作已完成：

* Places核心服務會出現在貴組織的Admin Console中。
* 您已被新增至組織。
* 您已被新增為組織中的Places核心服務的使用者。

   如需詳細資訊，請參閱 *新增使用者或開發人員至您的Places服務和Experience Platform Launch設定檔* 在 [取得Places Service的存取權](/help/places-gain-access.md).

* 您已被新增為組織中Places核心服務的開發人員。

   如需新增開發人員的詳細資訊，請參閱 *新增使用者或開發人員至您的Places服務和Experience Platform Launch設定檔* 在 [取得Places Service的存取權](/help/places-gain-access.md).

   如需開發人員角色的詳細資訊，請參閱 [管理開發人員](https://helpx.adobe.com/jp/enterprise/using/manage-developers.html).

### REST API要求

對Places Service REST API的每個請求都需要以下專案：

* 組織ID
* API金鑰
* 持有人權杖

與Adobe I/O的整合提供這些專案，以及使用JSON Web權杖(JWT)請求持有人權杖的方法。

* 如需JWT的詳細資訊，請參閱 [JSON Web Token簡介](https://jwt.io/introduction/).
* 若要建立Places Service的整合，請參閱 *建立Places服務整合* 區段底下。
* 若要瞭解API金鑰整合、產生JWT和公開金鑰憑證，請參閱 [Adobe I/O驗證概觀](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>如果您無法登入Adobe I/O主控台，或Places Service不是 *建立整合頁面*，請參閱 *組織需求* 在 [網站服務API總覽](/help/web-service-api/places-web-services.md).

## 建立Places服務整合

若要建立Places Service整合，請完成下列工作：

### 產生公開和私密金鑰組

若要建立Places Service整合，您需要公開和私密金鑰組。 您可以購買這些密碼組，或自行產生自行簽署的金鑰。

若要產生您自己的自行簽署金鑰：

1. 在終端機視窗中，複製並貼上下列各行，然後按下 **[!UICONTROL 輸入]** 貼上每一行後：

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >建議您為金鑰命名以方便參考，並將金鑰儲存在資料夾中。 如果您建立多個整合，可以輕鬆識別和管理哪些金鑰屬於哪個整合。

1. 輸入OpenSSL要求的資訊：

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   如需有關OpenSSL的詳細資訊，請參閱 [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >您提供的資訊會整合到索引鍵中。

1. 導覽至「 」所在目錄 `.key` 和 `.crt` 檔案的位置。

   例如，在MacOS中，前往 **[!UICONTROL Macintosh HD]** > **[!UICONTROL 使用者]** > **[!UICONTROL （您的使用者名稱）]** > **[!UICONTROL 金鑰]**.

以下影片會引導您完成產生金鑰組的程式：

![整合影片](/help/assets/places_integration_video.gif)

### 在Adobe I/O主控台中建立Places Service整合

若要建立Places Service整合：

1. 前往 [https://console.adobe.io](https://console.adobe.io) 並使用您的Adobe ID登入。
1. 在 **快速入門** 區段，按一下 **建立整合**.
1. 選取 **[!UICONTROL 存取API]** 並按一下 **[!UICONTROL 繼續]**.

   **[!UICONTROL 存取API]** 是預設位置。

1. 如果您擁有多個Experience Cloud組織的存取權，請從右上方的下拉式清單中選取組織。
1. 下 **[!UICONTROL Experience Cloud]**，選取 **[!UICONTROL Places Service]** 作為您想要整合的Adobe服務，然後按一下 **[!UICONTROL 繼續]**.
1. 選取 **[!UICONTROL 新整合]** 並按一下 **[!UICONTROL 繼續]**.
1. 在建立新整合畫面上，輸入名稱和說明。
1. 拖放 `xxxx_public.crt` 檔案（您在上面建立的）至 **[!UICONTROL 公開金鑰憑證]** 拖放區域。
1. 選取產品設定檔。

   如果您不確定要選取哪個設定檔，請聯絡您的系統管理員。
1. 在頁面底部，按一下 **[!UICONTROL 建立整合]**.
1. 幾秒後，在 *已建立整合* 畫面，確認出現下列訊息：

   `Your integration has been created.`

1. 整合詳細資訊頁面隨即顯示，整合的名稱位於頂端。

   此 **[!UICONTROL 概觀]** 索引標籤預設會出現，並顯示API金鑰、您的組織ID、技術帳戶ID以及有關您整合的其他詳細資訊。

### 記錄組織ID和API金鑰

1. 在整合詳細資訊頁面上，按一下 **[!UICONTROL 服務]** 標籤並確認 **[!UICONTROL Places Service]** 顯示於 **[!UICONTROL 已設定的服務]**.
1. 於 **[!UICONTROL 概觀]** 索引標籤，找到並記錄API金鑰（使用者端ID）和組織ID。

   每個Places Service REST API請求都需要這些ID。

![](/help/assets/places_orgid_api-key.png)

### 產生JWT權杖

在整合詳細資訊頁面上，按一下 **[!UICONTROL JWT]** 索引標籤來測試整合，方法是產生JWT並提供Exchange URL。

若要產生JWT權杖：

1. 在文字編輯器中，開啟 `private.key` 您在上面建立的檔案。
1. 在&#x200B;**[!UICONTROL 「JWT」]**&#x200B;標籤上&#x200B;**[!UICONTROL ，複製金鑰的內容並貼到]**「貼上私密金鑰」欄位中。
1. 按一下 **[!UICONTROL 產生JWT]**.
1. 在&#x200B;**[!UICONTROL 「Sample CURL 指令」]**&#x200B;區段中，按一下&#x200B;**[!UICONTROL 「複製」]**，然後將內容貼到命令提示字元或終端機視窗中。
1. 按下以執行命令 **[!UICONTROL 輸入]** 在鍵盤上。
1. 找到 `"token_type": "bearer"` 和 `"access_token"` 值。

   持有者存取權杖的值會用於您的Places服務API請求。

>[!IMPORTANT]
>
>Adobe存取權杖有效 **僅限** 24小時內，請儲存範例CURL指令（步驟5）。 如果存取權杖不再有效，您需要重新產生權杖。
