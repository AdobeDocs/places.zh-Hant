---
title: Adobe I/O整合概觀
description: 建立Adobe I/O整合的相關資訊。
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e

---


# 整合概觀和先決條件 {#integration-prereqs}

此資訊會告訴您如何建立Adobe I/O和Places服務整合。

## 使用者存取的先決條件

向組織的系統管理員確認下列任務已完成：

* 「置入核心服務」會顯示在您組織的管理控制台中。
* 您已加入組織。
* 您已新增為「將核心服務置於組織中的使用者」。

   如需詳細資訊，請參 *閱「取得Places服務的存取權」中的「將使用者或開發人員新增至您的Places服務和體驗平台啟動設定檔*[」](/help/places-gain-access.md)。

* 您已新增為「開發人員」，加入貴組織的「放置核心服務」。

   如需新增開發人員的詳細資訊，請參 *閱取得Places服務存取權中的「將使用者或開發人員新增至您的Places服務和Experience Platform Launch設定檔*[」](/help/places-gain-access.md)。

   如需開發人員角色的詳細資訊，請參閱「管 [理開發人員](https://helpx.adobe.com/enterprise/using/manage-developers.html)」。

### REST API請求

對Places Service REST API的每個請求都需要下列項目：

* 組織ID
* API金鑰
* 持牌代號

與Adobe I/O的整合提供這些項目，以及使用JSON網頁Token(JWT)來請求不記名Token的方式。

* 如需JWT的詳細資訊，請參 [閱JSON Web Token簡介](https://jwt.io/introduction/)。
* 要為Places服務建立整合，請參 *閱下面的建立Places服務整合* 。
* 若要瞭解API金鑰整合、產生JWT和公開金鑰憑證，請參閱 [Adobe I/O驗證概觀](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)。

>[!IMPORTANT]
>
>如果您無法登入Adobe I/O主控台，或如果「建立整合」頁面上不提供「置入服務」選項 *，請參閱「網站服務API概觀」中的「組織需求*」 **[](/help/web-service-api/places-web-services.md)。

## 建立Places服務整合

要建立Places服務整合，請完成以下任務：

### 生成公共密鑰對和私有密鑰對

若要建立Places service整合，您需要公用和私用金鑰對。 您可以購買這些對，也可以產生您自己的自簽金鑰。

若要產生您自己的自簽金鑰：

1. 在終端視窗中，複製並貼上下列每一行，並在貼上每 **[!UICONTROL Enter]**一行後按：

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >建議您命名索引鍵以方便參考，並將它們儲存在資料夾中。 如果您建立多個整合，您可以輕鬆識別和管理屬於哪個整合的金鑰。

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

   如需OpenSSL的詳細資訊，請參閱 [OpenSSL](https://www.openssl.org/)。

   >[!IMPORTANT]
   >
   >您提供的資訊會併入索引鍵中。

1. 導覽至和檔案所 `.key` 在 `.crt` 的目錄。

   例如，在MacOS中，請至 **[!UICONTROL Macintosh HD]**>**[!UICONTROL users]** > **[!UICONTROL (your user name)]**>**[!UICONTROL Keys]**。

以下視頻將引導您完成生成密鑰對的過程：

![整合視訊](/help/assets/places_integration_video.gif)

### 在Adobe I/O主控台中建立Places服務整合

要建立Places服務整合，請執行以下操作：

1. 請前往 [https://console.adobe.io](https://console.adobe.io) ，並使用您的Adobe ID登入。
1. 在「快速 **開始** 」區段中，按一下「 **建立整合」**。
1. 選擇 **[!UICONTROL Access an API]**並按一下**[!UICONTROL Continue]**。

   **[!UICONTROL Access an API]**是預設位置。

1. 如果您可以存取多個Experience cloud組織，請從右上角的下拉式清單中選取組織。
1. Under **[!UICONTROL Experience Cloud]**, select**[!UICONTROL Places Service]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. 選擇 **[!UICONTROL New integration]**並按一下**[!UICONTROL Continue]**。
1. 在「建立新整合」畫面中，輸入名稱和說明。
1. 將您在上方建 `xxxx_public.crt` 立的檔案拖放至拖放 **[!UICONTROL Public keys certificates]**區域。
1. 選擇產品設定檔。

   如果您不確定要選擇哪個配置檔案，請與系統管理員聯繫。
1. At the bottom of the page, click **[!UICONTROL Create integration]**.
1. 數秒後，在「已建立的整 *合」畫面中* ，確認出現下列訊息：

   `Your integration has been created.`

1. 此時會顯示整合詳細資訊頁面，其頂端是整合名稱。

   依預 **[!UICONTROL Overview]**設會顯示標籤，並顯示API金鑰、您的組織ID、技術帳戶ID，以及您整合的其他詳細資訊。

### 記錄組織ID和API金鑰

1. 在整合詳細資訊頁面上，按一下 **[!UICONTROL Services]**標籤並確認顯**[!UICONTROL Places Service]** 示於下方 **[!UICONTROL Configured Services]**。
1. 在標籤 **[!UICONTROL Overview]**上，找出並記錄API金鑰（用戶端ID）和組織ID。

   每個Places Service REST API請求都需要這些ID。

![](/help/assets/places_orgid_api-key.png)

### 產生JWT Token

在整合詳細資訊頁面上，按一 **[!UICONTROL JWT]**下標籤，以便您透過產生JWT並提供交換URL來測試整合。

要生成JWT令牌：

1. 在文字編輯器中，開啟您在上 `private.key` 方建立的檔案。
1. On the **[!UICONTROL JWT]**tab, copy the contents of the key and paste it in the**[!UICONTROL Paste private key]** field.
1. 按一下 **[!UICONTROL Generate JWT]**。
1. In the **[!UICONTROL Sample CURL command]**section, click**[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. 按鍵盤上的鍵 **[!UICONTROL Enter]**盤運行命令。
1. 找到 `"token_type": "bearer"` 和 `"access_token"` 值。

   載體存取Token的值是您在Places Service API請求中使用的值。

>[!IMPORTANT]
>
>Adobe存取Token的有效 **期限** 為24小時，請儲存範例CURL命令（步驟5）。 如果存取Token不再有效，您需要重新產生Token。