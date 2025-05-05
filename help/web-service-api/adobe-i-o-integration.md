---
title: Adobe Developer專案概觀
description: 有關建立Adobe Developer API專案的資訊。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Places API存取總覽和先決條件 {#developer-prereqs}

此資訊會說明如何在Adobe Developer Console中建立專案，並產生用於Places API要求的存取權杖。

## 使用者存取的必要條件

請向貴組織的系統管理員確認下列工作已完成：

* 您已被新增到組織。
* 您已被新增到Adobe Experience Platform中的設定檔。

  如需詳細資訊，請參閱[取得Places服務的存取權](/help/places-gain-access.md)中的&#x200B;*新增使用者或開發人員至您的Places服務並Experience Platform Launch設定檔*。

### REST API要求

對Places服務REST API的每個請求都需要以下專案：

* 組織ID
* API金鑰（也稱為使用者端ID）
* 使用者端密碼
* 持有人權杖

具有[Adobe Developer主控台](https://developer.adobe.com/console)的專案提供這些專案。

* 若要建立Places Service API的專案，請參閱下方的&#x200B;*建立Places Service專案*&#x200B;區段。

>[!IMPORTANT]
>
>如果您無法登入[Adobe Developer主控台](https://developer.adobe.com/console)，或如果&#x200B;*建立整合頁面*&#x200B;上的Places服務不是選項，請參閱[Web服務API總覽](/help/web-service-api/places-web-services.md)中的&#x200B;*組織需求*。

## 建立Places服務API專案

若要建立Places Service API專案，請完成下列操作：

1. 使用您的Adobe ID登入[Adobe Developer網站](https://developer.adobe.com)。
2. 按一下頁面右上角的&#x200B;**[!UICONTROL 主控台]**。
3. 如果您指派至多個Adobe組織，請從頁面右上角的下拉式清單中選取正確的組織。
4. 按一下&#x200B;**[!UICONTROL 建立新專案]**&#x200B;按鈕。
5. 按一下[開始使用新專案]區段中的[新增API] **&#x200B;**&#x200B;按鈕。
6. 若要選取Places API，請向下捲動頁面至Places卡片，然後按一下卡片右上角的核取方塊。
7. 按一下&#x200B;**[!UICONTROL 下一步]**&#x200B;按鈕。
8. 選取OAuth伺服器對伺服器選項（如果有選擇）。
9. 為認證命名，然後按一下&#x200B;**[!UICONTROL 下一步]**。
10. 選取設定檔（如果有多個設定檔，則任何設定檔都應該有效）。
11. 按一下[儲存並設定API]&#x200B;**&#x200B;**。
12. 在左側面板中，按一下「認證」底下的&#x200B;**[!UICONTROL OAuth伺服器對伺服器]**&#x200B;連結
13. 此頁面提供下列內容：
    * 產生存取權杖以用於Places服務REST API要求的方法。
    * 檢視curl命令的範例，瞭解如何從您自己的程式碼產生存取權杖。
    * 檢視使用者端ID （也稱為API金鑰）
    * 檢視使用者端密碼
    * 檢視組織識別碼
    * 向Places服務REST API提出的請求中需要上述所有專案。
14. 您可以按一下視窗左上角路徑中的專案名稱，將專案重新命名為較清楚描述的專案
15. 然後按一下頁面右上角的&#x200B;**[!UICONTROL 編輯專案]**&#x200B;按鈕。

>[!IMPORTANT]
>
>Adobe存取權杖僅&#x200B;**有效** 24小時，因此請儲存範例CURL命令（步驟5）。 如果存取權杖不再有效，您必須重新產生權杖。
