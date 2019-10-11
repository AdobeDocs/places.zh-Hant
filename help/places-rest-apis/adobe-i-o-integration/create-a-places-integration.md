---
title: 建立Places整合
seo-title: 建立Places整合
description: 有關建立Places整合的資訊。
seo-description: 有關建立Places整合的資訊。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 建立Places整合 {#create-places-integration}

若要建立Places整合，請完成下列工作：

## 生成公共密鑰對和私有密鑰對

若要建立Places整合，您需要公用和私用金鑰對。 您可以購買這些對，也可以產生您自己的自簽金鑰。

若要產生您自己的自簽金鑰：

1. 在終端視窗中，複製並貼上下列每一行，並在貼上每 **[!UICONTROL Enter]** 一行後按：

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >建議您命名索引鍵以方便參考，並將它們儲存在資料夾中。 如果您建立多個整合，您可以輕鬆識別和管理屬於哪個整合的金鑰。

2. 輸入OpenSSL要求的資訊：

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

3. 導覽至和檔案所 `.key` 在 `.crt` 的目錄。

   例如，在iOS中，請至 **[!UICONTROL Macintosh HD]** &gt; **[!UICONTROL users]** &gt; **[!UICONTROL (your user name)]** &gt; **[!UICONTROL Keys]**。

以下視頻將引導您完成生成密鑰對的過程：

![](/help/assets/places_integration_video.gif)

## 在Adobe I/O主控台中建立位置整合

要建立Places整合，請執行以下操作：

1. 請前往 [https://console.adobe.io](https://console.adobe.io) ，並使用您的Adobe ID登入。
2. 如果您可以存取多個Experience cloud組織，請從左側的下拉式清單中選取組織。
3. 按一下 **[!UICONTROL New Integration]**。
4. 選擇 **[!UICONTROL Access an API]** 並按一下 **[!UICONTROL Continue]**。
5. 在下 **[!UICONTROL Experience Cloud]**&#x200B;方，選 **[!UICONTROL Places]** 取您要整合的Adobe服務，然後按一下 **[!UICONTROL Continue]**。
6. 選擇 **[!UICONTROL New integration]** 並按一下 **[!UICONTROL Continue]**。
7. 在「建 *立新整合」畫面* ，輸入名稱和說明。
8. 將您在上方建 `xxxx_public.crt` 立的檔案拖放至拖放 **[!UICONTROL Public keys certificates]** 區域。
9. At the bottom of the page, click **[!UICONTROL Create integration]**.
10. 數秒後，在「已建立的整 *合」畫面中* ，確認出現下列訊息：

   `Your integration has been created.`

11. 按一下 **[!UICONTROL Continue to integration details]**。

   此時會顯示您與API金鑰、組織ID、技術帳戶ID的整合概觀，以及有關整合的其他詳細資訊。

## 記錄組織ID和API金鑰

1. 在標籤 **[!UICONTROL Services]** 上，確認已 **[!UICONTROL Places]** 顯示。
2. 在標籤 **[!UICONTROL Overview]** 上，找出並記錄API金鑰（用戶端ID）和組織ID。

   每個Places REST API請求都需要這些ID。

![](/help/assets/places_orgid_api-key.png)

## 產生JWT Token

在標 **[!UICONTROL JWT]** 簽上，Adobe I/O主控台可讓您產生JWT並提供交換URL，以測試您的整合。

要生成JWT令牌：

1. 在文字編輯器中，開啟您在上 `private.key` 方建立的檔案。
2. 在標 **[!UICONTROL JWT]** 簽上，複製索引鍵的內容並貼入欄 **[!UICONTROL Paste private key]** 位。
3. 按一下 **[!UICONTROL Generate JWT]**。
4. 在該節 **[!UICONTROL Sample CURL command]** 中，按一下並 **[!UICONTROL Copy]** 將內容貼上到命令提示符或終端窗口中。
5. 按鍵盤上的鍵 **[!UICONTROL Enter]** 盤運行命令。
6. 找到 `"token_type": "bearer"` 和 `"access_token"` 值。

   載體存取Token的值是您在Places API請求中使用的值。

>[!IMPORTANT]
>
>Adobe存取Token的有效 **期限** 為24小時，請儲存範例CURL命令（步驟5）。 如果存取Token不再有效，您需要重新產生Token。

