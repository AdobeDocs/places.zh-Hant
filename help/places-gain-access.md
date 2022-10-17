---
title: 獲得Places服務的訪問權
description: 本節提供有關如何將用戶添加到Places Service和Experience Platform Launch，以便用戶可以訪問Places Service的資訊。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# 獲得Places服務的訪問權 {#adding-user-launch-places}

Places Service現在可在資料收集UI中使用。 您可以從 [Adobe Experience Cloud首頁](https://experience.adobe.com).

![快速存取功能表](/help/assets/quickaccess.png)

您也可以從Adobe Experience Platform功能表存取資料收集：

![Experience Platform功能表](/help/assets/solutionaccessmenu.png)

如果您的使用者ID有存取權，您會在「資料收集中的資料管理」下方的左側面板中看到「Places Service」圖示，如下所示：

![資料收集左側面板](/help/assets/places_in_data_collection.png)

如果您在此位置看不到Places Service，請連絡貴組織的管理員，以在Admin Console中將您的使用者ID新增至Adobe Experience Platform。

## 新增使用者以存取Places Service和Experience Adobe Experience Platform資料收集

Places現已隨附於Adobe Experience Platform。 若要允許使用者存取 [Places Service](https://experience.adobe.com/#/data-collection/places)，則必須在Admin Console中以使用者身分新增至Adobe Experience Platform。 若要讓使用者擁有設定行動屬性和搭配Adobe Experience Platform SDK使用Places所需權限，才能存取Experience Platform資料收集，您也需要將使用者新增至Admin Console中的Adobe Experience Platform資料收集，並為Adobe Experience Platform資料收集指定下列權限：

* 「屬性權限」下的所有權限：
   * 核准
   * 開發
   * 編輯屬性
   * 管理環境
   * 管理擴充功能
   * 發佈
* 管理公司權限下的屬性權限

如果這是您第一次新增使用者，請完成下列步驟，將使用者新增至Adobe Experience Platform資料收集和Adobe Experience Platform。 如果您之前已新增使用者，可能會顯示多個設定檔，因此請務必選取正確的設定檔。

>[!IMPORTANT]
>
>只有組織管理員可以存取Admin Console並新增使用者。

### 1.確認已布建Adobe Experience Platform和Adobe Experience Platform資料收集

1. 登入您的Experience Cloud組織， [Adobe Experience Cloud首頁](https://experience.adobe.com).
1. 在右上角，按一下Experience Cloud殼層切換器以顯示下拉式功能表。

   ![殼切換器](/help/assets/places_shell_switcher1.png)

1. 在清單底部，按一下 **[!UICONTROL Admin Console]**. (連結至 **[!UICONTROL Admin Console]** 也可在「快速存取」區段中找到)。

   如果您沒有看到 **[!UICONTROL Admin Console]** 在清單中，您不是管理員。 您必須連絡組織管理員以完成此程式。

1. 在Admin Console中，如果您有數個組織的存取權，請確認在頁面右上角選取了正確的組織。

   這是您要新增使用者的組織。 如果尚未選取正確的組織，請按一下組織，然後從下拉式清單中選取正確的組織。

   >[!IMPORTANT]
   >
   >如果所需的組織不在下拉式清單中，表示您沒有該組織的管理員存取權。

1. 在Admin Console中，按一下產品標籤，並確認 **[!UICONTROL Adobe Experience Platform資料收集]** 和 **[!UICONTROL Adobe Experience Platform]** 的下界。

   ![](/help/assets/places_provisioned1.png)

   這2種產品會自動布建給所有組織，因此應該會出現。


### 2.新增使用者至這些產品

#### 添加用戶以提供對Places Service UI的訪問

1. 在產品標籤中，按一下 **[!UICONTROL Adobe Experience Platform]** 卡片。
2. 可將使用者新增至內的任何設定檔 **[!UICONTROL Adobe Experience Platform]** 若要存取Places，不需要設定特定權限。
3. 選擇一個配置檔案（如果有多個配置檔案），然後按一下它以開啟它。
4. 按一下藍色 **添加用戶** 按鈕，將使用者的AdobeID和名稱填入，然後按一下「儲存」以完成新增作業。

#### 新增使用者至資料收集

1. 在產品標籤中，按一下 **[!UICONTROL Adobe Experience Platform資料收集]** 卡片。
2. 依預設，名為 **預設資料收集全部存取** 將已建立。 向此設定檔新增使用者，將可確保他們擁有使用Places服務和資料收集的適當權限。 如果選取了不同的設定檔，請確定包括上述的權限。
3. 選擇一個配置檔案（如果有多個配置檔案），然後按一下它以開啟它。
4. 按一下藍色 **添加用戶** 按鈕，將使用者的AdobeID和名稱填入，然後按一下「儲存」以完成新增作業。

#### 新增使用者作為Places服務的開發人員。

若使用者同時需要存取Places Service REST API，您需將他們新增為開發人員。
1. 在產品標籤中，按一下 **[!UICONTROL Adobe Experience Platform]** 卡片。
2. 如果已將使用者新增至 **[!UICONTROL Adobe Experience Platform]** 透過上述指示卡片，選擇與先前使用的設定檔相同，然後按一下。
3. 在設定檔中，按一下 **開發人員** 標籤
4. 按一下藍色 **新增開發人員** 按鈕，將使用者的AdobeID和名稱填入，然後按一下「儲存」以完成新增作業。

完成上述步驟後，使用者會收到電子郵件，通知他們有存取權 **[!UICONTROL Adobe Experience Platform]** 和 **[!UICONTROL Adobe Experience Platform資料收集]**. 然後，他們可以登入 [Adobe Experience Cloud](https://experience.adobe.com) ，並訪問Places服務和資料收集。 如果您也完成步驟 **[!UICONTROL 新增開發人員]**，則使用者也可登入 [Adobe Developer Console](https://developer.adobe.com/console/home) 以建立專案，提供Places服務REST API的存取權。
