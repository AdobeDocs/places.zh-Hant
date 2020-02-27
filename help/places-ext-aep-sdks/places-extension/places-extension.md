---
title: Places 擴充功能
description: Places擴充功能可讓您根據使用者的位置採取行動。
translation-type: tm+mt
source-git-commit: 36ea8616aa05f5b825a2a4c791a00c5b3f332e9f

---


# Places 擴充功能 {#places-extension}

Places擴充功能可讓您根據使用者的位置採取行動。 此擴充功能是Places Query Service API的介面。 透過監聽包含GPS座標和地理區域事件的事件，此擴充功能會派送規則引擎處理的新事件。 Places擴充功能也會擷取並傳送從API擷取之應用程式資料的最近POI清單。 API傳回的區域會儲存在快取和永續性中，允許有限的離線處理。

## 在Adobe Experience Platform Launch中安裝Places擴充功能

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. 在標籤 **[!UICONTROL Catalog]** 上，找到擴 **[!UICONTROL Places]** 展名，然後按一下 **[!UICONTROL Install]**。
1. 選擇要在此屬性中使用的「置入」庫。 這些是您應用程式中可存取的資料庫。
1. 按一下 **[!UICONTROL Save]**。

   當您按一 **[!UICONTROL Save]**&#x200B;下，Experience Platform SDK會在您選取的程式庫中，搜尋Places Services中的POI。 當您建立應用程式時，POI資料不會包含在程式庫的下載中，但POI的位置子集會在執行時期下載至使用者裝置，並以使用者的GPS座標為基礎。

1. 完成發佈程式以更新SDK組態。

   如需有關在Experience Platform Launch中發佈的詳細資訊，請參閱 [發佈](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html)。

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

   或者，如果您不使用Cocoapods，則可從Github的發行頁面手動加入Mobile Core和 [Places程式庫](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) 。

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

### 使用Mobile Core註冊Places擴充功能 {#register-places-mobile-core}

您必須在Android和iOS中使用Mobile Core註冊Places擴充功能。

#### Android

在您應用程式的方 `OnCreate` 法中，註冊Places擴充功能：

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

### 修改「地點」會籍的上線時間 {#places-ttl}

位置資料可能會很快過時，尤其是當裝置未收到背景位置更新時。

設定設定，以控制裝置上放置會籍資料的上線 `places.membershipttl` 時間。 傳入的值代表「置入」狀態對裝置維持有效的秒數。

#### Android

在回呼中， `MobileCore.start()` 在呼叫前使用必要的變更更新設定 `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

在回呼方法的第一行 `ACPCore`中， `start:` 調用 `updateConfiguration:`

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## 配置密鑰

若要在執行時期以程式設計方式更新SDK組態，請使用下列資訊來變更您的Places擴充功能組態值。 如需詳細資訊，請參 [閱設定API參考](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| 代碼 | 必填 | 說明 |
| :--- | :--- | :--- |
| `places.libraries` | 是 | 行動應用程式的Places擴充功能程式庫。 它會指定行動應用程式支援的程式庫ID和程式庫名稱。 |
| `places.endpoint` | 是 | 預設的Places Query service端點，用於獲取有關庫和POI的資訊。 |
| `places.membershipttl` | 無 | 預設值3600（一小時內的秒數）。 指出裝置的「置入」會籍資訊的有效期（以秒為單位）。 |
