---
title: Places 擴充功能
description: Places擴充功能可讓您根據使用者的位置採取行動。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Places 擴充功能 {#places-extension}

Places擴充功能可讓您根據使用者的位置採取行動。 此擴充功能是Places Query Service API的介面。 透過監聽包含GPS座標和地理區域事件的事件，此擴充功能會派送規則引擎處理的新事件。 Places擴充功能也會擷取並傳送從API擷取之應用程式資料的最近POI清單。 API傳回的區域會儲存在快取和永續性中，允許有限的離線處理。

## 在Adobe Experience Platform Launch中安裝Places擴充功能

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]**tab.
1. 在標籤 **[!UICONTROL Catalog]**上，找到擴**[!UICONTROL Places]** 展名，然後按一下 **[!UICONTROL Install]**。
1. 選擇要在此屬性中使用的「置入」庫。 這些是您應用程式中可存取的資料庫。
1. 按一下 **[!UICONTROL Save]**。

   當您按一 **[!UICONTROL Save]**下，Experience Platform SDK會在您選取的程式庫中，搜尋Places Services中的POI。 當您建立應用程式時，POI資料不會包含在程式庫的下載中，但POI的位置子集會在執行時期下載至使用者裝置，並以使用者的GPS座標為基礎。

1. 完成發佈程式以更新SDK組態。

   如需有關在Experience Platform Launch中發佈的詳細資訊，請參閱 [發佈](https://docs.adobelaunch.com/launch-reference/publishing)。

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## 將Places擴充功能新增至您的應用程式 {#add-places-to-app}

您可以將Places擴充功能新增至Android和iOS應用程式。

### Android

若要使用Java將Places擴充功能新增至您的應用程式：

1. 使用應用程式的Gradle檔案，將Places擴充功能新增至您的專案。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. 在應用程式的主要活動中匯入「位置」擴充功能。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

若要使用Objective-C或Swift將Places擴充功能新增至您的應用程式：

1. 將「地標」和「 [行動核心](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) 」程式庫新增至您的專案。 您需要將下列Pod新增至您的 `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   或者，如果您不使用Cocoapods，則可以從Github的發行頁面手動加入Mobile Core [和](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) Places程式庫。

1. 更新您的Cocoapod:

   ```objective-c
   pod update
   ```

1. 開啟Xcode，然後在您的AppDelegate類別中匯入「核心」和「位置」標題：

   **Objective-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### 使用行動核心註冊地標 {#register-places-mobile-core}

您必須在Android和iOS中使用Mobile Core註冊地標。

#### Android

在您應用程式的方 `OnCreate` 法中註冊位置服務擴充功能：

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

在您的應用程式方 `application:didFinishLaunchingWithOptions:` 法中，將Places擴充功能註冊至您的其他SDK註冊呼叫：

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

## 配置密鑰

若要在執行時期以程式設計方式更新SDK組態，請使用下列資訊來變更您的Places組態值。 如需詳細資訊，請參 [閱設定API參考](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| 代碼 | 必填 | 說明 |
| :--- | :--- | :--- |
| `places.libraries` | 是 | 行動應用程式的位置資料庫。 它會指定行動應用程式支援的程式庫ID和程式庫名稱。 |
| `places.endpoint` | 是 | 預設的Experience Platform位置查詢服務端點，用來取得資料庫和POI的相關資訊。 |

