---
title: 存取Adobe Experience Platform Location Service
seo-title: 存取Adobe Experience Platform Location Service
description: 本節提供如何將使用者新增至定位服務和體驗平台啟動的相關資訊，讓使用者能夠存取定位服務。
seo-description: 本節提供如何將使用者新增至定位服務和體驗平台啟動的相關資訊，讓使用者能夠存取定位服務。
translation-type: tm+mt
source-git-commit: 1b4482c8e4cf825c0182421fe00f8b86b411c11b

---


# 存取Adobe Experience Platform Location Service {#adding-user-launch-places}

您可以從 [Adobe Experience cloud首頁的快速存取功能表存取平台位置服務](https://experience.adobe.com)。
如果您的使用者ID有存取權，您會看到「位置服務」圖示，如下所示：

![快速存取選單](/help/assets/quick-access.png)

您也可以從Adobe Experience platform選單存取平台位置服務：

![體驗平台功能表](/help/assets/exp-platform-menu-sm.png)

如果您在其中任一功能表中都未看到平台位置服務，您將需要連絡組織內的管理員，以將您的使用者ID新增至管理控制台中的Places核心服務。

## 新增使用者至位置服務與體驗平台啟動

若要允許使用者存 [取Launch Service UI](https://places.adobe.com)，他們必須以使用者身分新增至Admin Console的Places Core Service。 若要讓使用者能夠存取Experience Platform Launch、設定行動裝置屬性，以及搭配Adobe Experience Platform SDK使用Places，他們必須新增至Admin Console的Experience Platform Launch，並獲得下列Experience Platform Launch權限：

* 所有產權：
   * 開發
   * 核准
   * Publish
   * 管理擴充功能
   * 管理環境
* 管理公司權限下的屬性權限

如果這是您第一次新增使用者，請完成下列步驟，將使用者新增至Experience Platform Launch and Location Service。 如果您之前已新增使用者，可能會顯示多個描述檔，因此請確定您選取的是正確的描述檔。

>[!IMPORTANT]
>
>只有組織管理員才能存取Admin Console並新增使用者。

### 1.確認已布建位置服務和體驗平台啟動

若要確認已布建位置服務和體驗平台啟動：

1. 登入您的Experience cloud組織。
1. 在右上方，按一下Experience cloud殼層切換器。

   ![殼切換器](/help/assets/places_shell_switcher1.png)

1. 在 **[!UICONTROL Platform]** 底下，按一下 **[!UICONTROL Administration]**。

   如果您未在清單中 **看到** 「管理」，表示您不是管理員。 您必須連絡組織管理員才能完成此程式。

1. 在「Experience cloud管理」頁面中，按一 **[!UICONTROL Admin Console]** 下卡片上的 **[!UICONTROL Take me there]**。

1. 在「管理控制台」中，如果您有權存取數個組織，請確認在頁面的右上方選取了正確的組織。

   這是您要新增使用者的組織。 如果尚未選擇正確的組織，請按一下組織並從下拉清單中選擇組織。

   >[!IMPORTANT]
   >
   >如果您沒有組織的存取權，表示您沒有該組織的管理員存取權。

1. 驗證是否顯示 **[!UICONTROL Adobe Experience Platform Launch]** 和 **[!UICONTROL Places Core Services]** 的卡。

   ![](/help/assets/places_provisioned1.png)

   如果顯示，您的組織已布建「位置服務」和「體驗平台啟動」。 如果未顯示，則需要為您的組織布建。


### 2.設定描述檔並新增權限

若要設定描述檔並新增權限：

1. 設定Experience Platform Launch設定檔，讓已新增至設定檔的使用者可透過Experience Platform SDK使用Experience Platform Launch及其行動裝置屬性。

   a.在菜單欄中，按一下 **[!UICONTROL Product]**。

   b.在左窗格的產品清單中，按一下 **[!UICONTROL Adobe Experience Platform Launch]**。

   * Experience Platform Launch設定檔會顯示在右側。
   * Experience Platform Launch的預設描述檔名為 *Launch -（組織名稱）* 。

      如果您先前已將使用者新增至Experience Platform Launch，您可能會看到列出多個描述檔。

1. 選擇正確的配置檔案：

   a.按一下預設配置檔案的名稱。

   b.按一下標 **[!UICONTROL Permissions]** 簽。

   c.按一 **[!UICONTROL Edit]** 下旁邊 **[!UICONTROL Property Rights]**。

   d.在左窗格中，按一下 **[!UICONTROL + Add all]**。

   此步驟會將所有可用權限移至包含的權限清單。

   e.按一 **[!UICONTROL Company Rights]**&#x200B;下。

   f.在左窗格中，按一下 **[!UICONTROL + Manage Properties]**。

   g.按一 **[!UICONTROL Save]**&#x200B;下。

>[!IMPORTANT]
>
>對於位置服務，有預設的描述檔，但您不需要新增任何權限。

您已成功新增權限至您建立的描述檔。

### 3.將使用者或開發人員新增至您的位置服務與體驗平台啟動設定檔

您可以將使用者和／或開發人員新增至您的位置服務和體驗平台啟動設定檔。

### 新增使用者

若要將使用者新增至您的位置服務與體驗平台啟動設定檔：

1. 新增使用者至Experience Platform Launch設定檔。

   a.在菜單欄中，按一下 **[!UICONTROL Overview]**。

   b.在卡 **[!UICONTROL Adobe Experience Platform Launch]** 上驗證以下內容：

   * 卡片底部會顯示兩個點。
   * 左邊的圓點是黑色的。

      如果右邊的點是黑色，則只能新增開發人員。 若要新增使用者，請按一下左側的點。
   c.按一 **[!UICONTROL + Add Users]**&#x200B;下。

   d.輸入使用者的Adobe ID。

   e.完成下列步驟之一：

   * 如果您要新增使用者，請按一 **[!UICONTROL New user]**&#x200B;下，然後輸入使用者的名字和姓氏。
   * 如果您要新增現有使用者，請按一下所顯示的使用者名稱。
   f.在下拉 **[!UICONTROL Please select a profile for this product]** 式清單中，選取您先前編輯的描述檔。

   g.按一 **[!UICONTROL Save]**&#x200B;下。

1. 新增使用者至 **[!UICONTROL Places Core Services]**。

   >[!TIP]
   >
   >目前，所有位置服務使用者都有相同的權限，因此您不需要編輯權限。

   a.在卡 **[!UICONTROL Places Core Services]** 上驗證以下內容：

   * 卡片底部會顯示兩個點。
   * 左邊的圓點是黑色的。
   b.按一 **[!UICONTROL + Assign Users]**&#x200B;下。

   c.輸入使用者的Adobe ID。

   d.完成下列步驟之一：

   * 如果您要新增使用者，請按一 **[!UICONTROL New user]**&#x200B;下，然後輸入使用者的名字和姓氏。
   * 如果您要新增現有使用者，請按一下所顯示的使用者名稱。
   e.在下拉 **[!UICONTROL Please select a profile for this product]** 式清單中，選取「位置」描述檔。

   f.按一 **[!UICONTROL Save]**&#x200B;下。

### 新增開發人員

對於需要存取網站服務API的使用者，您必須以開發人員身分加入。

若要新增開發人員：

1. 在卡 **[!UICONTROL Places Core Services]** 上驗證以下內容：

   * 卡片底部會顯示兩個點。
   * 按一下右側的點， **[!UICONTROL Assign Developers]** 卡片底部便會出現。

1. 按一下 **[!UICONTROL + Assign Developers]**。

1. 輸入使用者的 Adobe ID。

1. 完成下列其中一個步驟:

   * 如果您要新增使用者，請按一 **[!UICONTROL New user]** 下並輸入使用者的名字和姓氏。
   * 如果您要新增現有使用者，請按一下所顯示的使用者名稱。

1. 在下拉 **[!UICONTROL Please select a profile for this product]** 式清單中，選取「位置服務」描述檔。

1. 按一下&#x200B;**「儲存」**。

使用者會收到電子郵件，通知他們具有 Experience Platform Launch 的存取權。他們可以登入此組織的 [Experience Platform Launch](https://launch.adobe.com) 或 [Places](https://places.adobe.com) 使用者介面。如果您完成&#x200B;**「新增開發人員」**&#x200B;程序中的步驟 4，則使用者也可登入 [Adobe I/O 主控台](https://console.adobe.io)，以建立 Places 整合，並使用 Places REST API。
