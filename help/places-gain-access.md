---
title: '存取Places服務 '
description: 本節提供如何將用戶添加到Places服務和Experience Platform Launch中，以便用戶訪問Places服務的相關資訊。
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 9%

---

# 獲得對Places服務{#adding-user-launch-places}的訪問權

您可以從[Adobe Experience Cloud家庭](https://experience.adobe.com)的快速訪問菜單訪問Places服務。
如果您的使用者ID有存取權，您會看到「Places Service」圖示，如下所示：

![快速存取選單](/help/assets/quickaccess.png)

您也可以從Adobe Experience Platform菜單訪問Places服務：

![Experience Platform菜單](/help/assets/solutionaccessmenu.png)

如果您在其中任一功能表中都未看到Places服務，請連絡您組織的管理員，將您的使用者ID新增至Admin Console中的Places Core Service。

## 將用戶添加到放置服務和Experience Platform Launch

要允許用戶訪問[Experience Platform LaunchUI](https://launch.adobe.com)，他們需要以用戶身份添加到Admin Console中的「放置核心服務」。 若要允許使用者存取Experience Platform Launch、設定行動裝置屬性，以及搭配Adobe Experience PlatformSDK使用地標，他們必須新增至Admin Console中的Experience Platform Launch，並獲得下列Experience Platform Launch權限：

* 所有產權：
   * 開發
   * 核准
   * 發佈
   * 管理擴充功能
   * 管理環境
* 管理公司權限下的屬性權限

如果這是您第一次新增使用者，請完成下列步驟，將使用者新增至Experience Platform Launch和放置服務。 如果您之前已新增使用者，可能會顯示多個描述檔，因此請確定您選取的是正確的描述檔。

>[!IMPORTANT]
>
>只有組織管理員才能存取Admin Console並新增使用者。

### 1.驗證是否已布建Places服務和Experience Platform Launch

1. 登入您的Experience Cloud組織。
1. 在右上側，按一下Experience Cloud殼切換器。

   ![殼切換器](/help/assets/places_shell_switcher1.png)

1. 在&#x200B;**[!UICONTROL Platform]**&#x200B;下，按一下&#x200B;**[!UICONTROL Administration]**。

   如果您在清單中未看到&#x200B;**[!UICONTROL 管理]**，則您不是管理員。 您必須連絡組織管理員才能完成此程式。

1. 在「Experience Cloud管理」頁面的&#x200B;**[!UICONTROL Admin Console]**&#x200B;卡上，按一下&#x200B;**[!UICONTROL 將我帶到]**。

1. 在Admin Console中，如果您有權存取數個組織，請確認在頁面的右上方選取了正確的組織。

   這是您要新增使用者的組織。 如果尚未選擇正確的組織，請按一下組織並從下拉清單中選擇組織。

   >[!IMPORTANT]
   >
   >如果您沒有組織的存取權，表示您沒有該組織的管理員存取權。

1. 確認已顯示 **[!UICONTROL Adobe Experience Platform Launch]** 與 **[!UICONTROL Places 核心服務]**&#x200B;的卡片。

   ![](/help/assets/places_provisioned1.png)

   如果顯示這些項目，則已為您的組織布建「地點服務」和「Experience Platform Launch」。 如果未顯示，則需要為您的組織布建。


### 2.設定描述檔並新增權限

1. 設定Experience Platform Launch描述檔，可讓新增至描述檔的使用者，將Experience Platform Launch及其行動屬性與Experience PlatformSDK搭配使用。

   a.在菜單欄中，按一下&#x200B;**[!UICONTROL Product]**。

   b.在左窗格的產品清單中，按一下&#x200B;**[!UICONTROL Adobe Experience Platform Launch]**。

   * Experience Platform Launch配置檔案顯示在右側。
   * Experience Platform Launch有一個名為&#x200B;*Launch -（組織名稱）*&#x200B;的預設配置檔案。

      如果您先前已將使用者新增至Experience Platform Launch，您可能會看到列出多個描述檔。

1. 選擇正確的配置檔案：

   a.按一下預設配置檔案的名稱。

   b.按一下&#x200B;**[!UICONTROL 權限]**&#x200B;頁籤。

   c. 按一下&#x200B;**[!UICONTROL 「屬性權利」]**&#x200B;旁的&#x200B;**[!UICONTROL 「編輯」]**。

   d.在左窗格中，按一下&#x200B;**[!UICONTROL + Add all]**。

   此步驟會將所有可用權限移至包含的權限清單。

   e.按一下&#x200B;**[!UICONTROL 公司權利]**。

   f.在左窗格中，按一下&#x200B;**[!UICONTROL +管理屬性]**。

   g. 按一下&#x200B;**[!UICONTROL 儲存]**。

>[!IMPORTANT]
>
>對於「地標服務」，有預設的描述檔，但您不需要新增任何權限。

您已成功新增權限至您建立的描述檔。

### 3.將使用者或開發人員新增至您的Places服務和Experience Platform Launch設定檔

您可以將使用者和／或開發人員新增至您的Places服務和Experience Platform Launch設定檔。

### 新增使用者

要將用戶添加到您的Places服務和Experience Platform Launch配置檔案中，請執行以下操作：

1. 新增使用者至Experience Platform Launch描述檔。

   a.在菜單欄中，按一下&#x200B;**[!UICONTROL 概述]**。

   b.在&#x200B;**[!UICONTROL Adobe Experience Platform Launch]**&#x200B;卡上，驗證以下內容：

   * 卡片底部會顯示兩個點。
   * 左邊的圓點是黑色的。

      如果右邊的點是黑色，則只能新增開發人員。 若要新增使用者，請按一下左側的點。
   c.按一下&#x200B;**[!UICONTROL + 「添加用戶」]**。

   d.輸入使用者的Adobe ID。

   e.完成下列步驟之一：

   * 如果您要新增使用者，請按一下「新增使用者」，然後輸入使用者的名字和姓氏。****
   * 如果您要新增現有使用者，請按一下所顯示的使用者名稱。

   f.在&#x200B;**[!UICONTROL 請為此產品]**&#x200B;下拉式清單中，選擇您先前編輯的描述檔。

   g. 按一下&#x200B;**[!UICONTROL 儲存]**。

1. 將用戶添加到&#x200B;**[!UICONTROL 放置核心服務]**。

   >[!TIP]
   >
   >目前，所有Places Service使用者都有相同的權限，因此您不需要編輯權限。

   a.在&#x200B;**[!UICONTROL 放置核心服務]**&#x200B;卡上，驗證以下內容：

   * 卡片底部會顯示兩個點。
   * 左邊的圓點是黑色的。

   b.按一下&#x200B;**[!UICONTROL + Assign Users]**。

   c.輸入使用者的Adobe ID。

   d.完成下列步驟之一：

   * 如果您要新增使用者，請按一下「新增使用者」，然後輸入使用者的名字和姓氏。****
   * 如果您要新增現有使用者，請按一下所顯示的使用者名稱。

   e.在&#x200B;**[!UICONTROL 請為此產品]**&#x200B;下拉式清單選擇配置式，選擇「位置」配置式。

   f. 按一下&#x200B;**[!UICONTROL 儲存]**。

### 新增開發人員

對於需要存取網站服務API的使用者，您必須以開發人員身分加入。

若要新增開發人員：

1. 在&#x200B;**[!UICONTROL 「Places 核心服務」]**&#x200B;卡上，驗證以下內容：

   * 卡片底部會顯示兩個點。
   * 按一下右側的點，**[!UICONTROL 指派開發人員]**&#x200B;就會出現在資訊卡的底部。

1. 按一下「**[!UICONTROL +指派開發人員]**」。

1. 輸入使用者的 Adobe ID。

1. 完成下列其中一個步驟：

   * 如果您要新增使用者，請按一下「新增使用者」，然後輸入使用者的名字和姓氏。****
   * 如果您要新增現有使用者，請按一下所顯示的使用者名稱。

1. 在&#x200B;**[!UICONTROL 請為此產品]**&#x200B;下拉式清單選擇配置式，選擇「放置服務」配置式。

1. 按一下&#x200B;**[!UICONTROL 「儲存」]**。

使用者會收到電子郵件，通知他們具有 Experience Platform Launch 的存取權。他們可以登入此組織的[Experience Platform Launch](https://launch.adobe.com)或[放置服務](https://places.adobe.com) UI。 如果您完成&#x200B;**[!UICONTROL 「新增開發人員」]**&#x200B;程序中的步驟 4，則使用者也可登入 [Adobe I/O 主控台](https://console.adobe.io)，以建立 Places 整合，並使用 Places REST API。
