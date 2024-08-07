---
title: 取得Places Service的存取權
description: 本節提供如何新增使用者至Places服務與Experience Platform Launch，讓使用者可以存取Places服務的相關資訊。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# 取得Places Service的存取權 {#adding-user-launch-places}

Places服務現在可在資料收集UI中使用。 您可以從[Adobe Experience Cloud首頁](https://experience.adobe.com)上的快速存取功能表存取資料集合。

![快速存取功能表](/help/assets/quickaccess.png)

您也可以從Adobe Experience Platform功能表存取「資料收集」：

![Experience Platform功能表](/help/assets/solutionaccessmenu.png)

如果您的使用者ID擁有存取權，您將會在資料收集的資料管理下方的左側面板中看到Places Service圖示，如下所示：

![資料收集左側面板](/help/assets/places_in_data_collection.png)

如果您在此位置看不到Places服務，請聯絡貴組織的管理員，在Admin Console中將您的使用者ID新增至Adobe Experience Platform。

## 新增使用者以存取Places服務和Experience Adobe Experience Platform資料收集

Places現已納入Adobe Experience Platform。 若要允許使用者存取[Places服務](https://experience.adobe.com/#/data-collection/places)，需要以使用者的身分將其新增至Admin Console中的Adobe Experience Platform。 若要讓使用者有權存取Experience Platform資料收集，並取得設定行動屬性及搭配Adobe Experience Platform SDK使用Places所需的許可權，他們也需要在Admin Console中新增至Adobe Experience Platform資料收集，並獲得Adobe Experience Platform資料收集的下列許可權：

* 「屬性權利」底下的所有許可權：
   * 核准
   * 開發
   * 編輯屬性
   * 管理環境
   * 管理擴充功能
   * 發佈
* 「公司權利」下的「管理屬性」許可權

如果您是第一次新增使用者，請完成下列步驟，將使用者新增至Adobe Experience Platform資料收集和Adobe Experience Platform。 如果您之前已新增使用者，可能會顯示多個設定檔，因此請確定您選取正確的設定檔。

>[!IMPORTANT]
>
>只有組織管理員可以存取Admin Console並新增使用者。

### 1.確認已布建Adobe Experience Platform和Adobe Experience Platform資料彙集

1. 登入您的Experience Cloud組織[Adobe Experience Cloud首頁](https://experience.adobe.com)。
1. 在右上角，按一下Experience Cloud殼層切換器以顯示下拉式功能表。

   ![殼層切換器](/help/assets/places_shell_switcher1.png)

1. 在清單底部，按一下&#x200B;**[!UICONTROL Admin Console]**。 (在「快速存取」區段中也可以找到&#x200B;**[!UICONTROL Admin Console]**&#x200B;的連結)。

   如果您在清單中看不到&#x200B;**[!UICONTROL Admin Console]**，則表示您不是管理員。 您必須連絡組織管理員，才能完成此程式。

1. 在Admin Console中，如果您擁有數個組織的存取權，請確認已在頁面的右上角選取正確的組織。

   這是您將新增使用者的組織。 如果尚未選取正確的組織，請按一下組織，然後從下拉式清單中選取正確的組織。

   >[!IMPORTANT]
   >
   >如果需要的組織不在下拉式清單中，這表示您沒有該組織的管理員存取權。

1. 在Admin Console中，按一下[產品]索引標籤，然後確認已顯示&#x200B;**[!UICONTROL Adobe Experience Platform Data Collection]**&#x200B;和&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;的卡片。

   ![](/help/assets/places_provisioned1.png)

   這2項產品會自動布建至所有組織，因此應該都會出現。


### 2.將使用者新增至這些產品

#### 新增使用者以提供Places服務UI的存取權

1. 在[產品]索引標籤中，按一下&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;卡片。
2. 使用者可以新增至&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;內的任何設定檔，以存取地標，不需要設定特定許可權。
3. 選擇設定檔（如果有多個設定檔），然後按一下以開啟設定檔。
4. 按一下藍色的&#x200B;**新增使用者**&#x200B;按鈕，將使用者的AdobeID和名稱填入，然後按一下「儲存」以完成新增。

#### 將使用者新增至資料收集

1. 在[產品]索引標籤中，按一下&#x200B;**[!UICONTROL Adobe Experience Platform Data Collection]**&#x200B;卡片。
2. 預設會建立名為&#x200B;**預設資料收集所有存取**&#x200B;的設定檔。 將使用者新增至此設定檔將確保他們擁有使用Places服務和資料收集的適當許可權。 如果選擇其他設定檔，請確定包含上述許可權。
3. 選擇設定檔（如果有多個設定檔），然後按一下以開啟設定檔。
4. 按一下藍色的&#x200B;**新增使用者**&#x200B;按鈕，將使用者的AdobeID和名稱填入，然後按一下「儲存」以完成新增。

#### 新增使用者作為Places Service的開發人員。

若使用者也需要Places Service REST API的存取權，您需要將其新增為開發人員。
1. 在[產品]索引標籤中，按一下&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;卡片。
2. 如果使用者已透過上述指示新增至&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;卡片，請選擇相同的先前使用設定檔，然後按一下該設定檔。
3. 在設定檔中，按一下&#x200B;**開發人員**&#x200B;標籤
4. 按一下藍色的&#x200B;**新增開發人員**&#x200B;按鈕，將使用者的AdobeID和名稱填入，然後按一下「儲存」以完成新增。

完成上述步驟後，使用者將會收到電子郵件，通知他們擁有&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;和&#x200B;**[!UICONTROL Adobe Experience Platform資料彙集]**&#x200B;的存取權。 接著，他們可以登入此組織的[Adobe Experience Cloud](https://experience.adobe.com)，並存取Places服務和資料收集。 如果您也完成步驟&#x200B;**[!UICONTROL 新增開發人員]**，使用者也可以登入[Adobe Developer Console](https://developer.adobe.com/console/home)，以建立可存取Places Service REST API的專案。
