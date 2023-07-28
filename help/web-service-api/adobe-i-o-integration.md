---
title: Adobe Developer專案概觀
description: 有關建立Adobe Developer API專案的資訊。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Places API存取總覽和先決條件 {#developer-prereqs}

此資訊說明如何在Adobe Developer主控台中建立專案，並產生用於Places API要求的存取權杖。

## 使用者存取的必要條件

請向貴組織的系統管理員確認下列工作已完成：

* 您已被新增到組織。
* 您已被新增到Adobe Experience Platform中的設定檔。

  如需詳細資訊，請參閱 *新增使用者或開發人員至您的Places Service和Experience Platform Launch設定檔* 在 [取得Places Service的存取權](/help/places-gain-access.md).

### REST API要求

對Places服務REST API的每個請求都需要以下專案：

* 組織ID
* API金鑰（也稱為使用者端ID）
* 使用者端密碼
* 持有人權杖

具有下列專案的專案 [Adobe Developer主控台](https://developer.adobe.com/console) 提供這些專案。

* 若要建立Places Service API專案，請參閱 *建立Places Service專案* 一節。

>[!IMPORTANT]
>
>如果您無法登入 [Adobe Developer主控台](https://developer.adobe.com/console)，或若在 *建立整合頁面*，請參閱 *組織需求* 在 [網站服務API總覽](/help/web-service-api/places-web-services.md).

## 建立Places服務API專案

若要建立Places Service API專案，請完成下列操作：

1. 登入 [Adobe Developer網站](https://developer.adobe.com) 使用您的Adobe ID。
2. 按一下 **[!UICONTROL 主控台]** 在頁面的右上角。
3. 如果您指派至多個Adobe組織，請從頁面右上角的下拉式清單中選取正確的組織。
4. 按一下 **[!UICONTROL 建立新專案]** 按鈕。
5. 按一下 **[!UICONTROL 新增API]** 開始使用新專案區段中的按鈕。
6. 若要選取Places API，請向下捲動頁面至Places卡片，然後按一下卡片右上角的核取方塊。
7. 按&#x200B;**[!UICONTROL 下一步]**&#x200B;按鈕.
8. 選取OAuth伺服器對伺服器選項（如果有選擇）。
9. 命名認證並按一下 **[!UICONTROL 下一個]**.
10. 選取設定檔（如果有多個設定檔，則任何設定檔都應該有效）。
11. 按一下 **[!UICONTROL 儲存並設定API]**.
12. 在左側面板中，按一下 **[!UICONTROL OAuth伺服器對伺服器]** 憑證下的連結
13. 此頁面提供下列內容：
   * 產生存取權杖以用於Places服務REST API要求的方法。
   * 檢視curl命令的範例，瞭解如何從您自己的程式碼產生存取權杖。
   * 檢視使用者端ID （也稱為API金鑰）
   * 檢視使用者端密碼
   * 檢視組織識別碼
   * 向Places服務REST API提出的請求中需要上述所有專案。
14. 您可以按一下視窗左上角路徑中的專案名稱，將專案重新命名為較清楚描述的專案
15. 然後按一下 **[!UICONTROL 編輯專案]** 按鈕來切換頁面。

>[!IMPORTANT]
>
>Adobe存取權杖有效 **僅限** 24小時內，請儲存範例CURL指令（步驟5）。 如果存取權杖不再有效，您必須重新產生權杖。
