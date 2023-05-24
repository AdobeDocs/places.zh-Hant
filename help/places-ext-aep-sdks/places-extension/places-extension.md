---
title: Places 擴充功能
description: Places擴充功能可讓您根據使用者的位置採取行動。
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: 795808b38851d5afcedc03f58e9a1d6342830934
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 5%

---

# Places 擴充功能 {#places-extension}

Places擴充功能可讓您根據使用者的位置採取行動。 此擴充功能是Places查詢服務API的介面。 透過接聽包含GPS座標和地理圍欄區域事件的事件，此擴充功能會傳送由規則引擎處理的新事件。 Places擴充功能也會擷取並傳送從API擷取之應用程式資料的最近POI清單。 API傳回的區域會儲存在快取和持續性中，以允許有限的離線處理。

## 在Adobe Experience Platform Launch中安裝Places擴充功能

1. 在Experience Platform Launch中，按一下 **[!UICONTROL 擴充功能]** 標籤。
1. 於 **[!UICONTROL 目錄]** 索引標籤中，找到 **[!UICONTROL 地點]** 擴充功能上，然後按一下 **[!UICONTROL 安裝]**.
1. 選取您要在此屬性中使用的Places資料庫。 這些是可在您的應用程式中存取的程式庫。
1. 按一下&#x200B;**[!UICONTROL 儲存]**。

   當您按一下 **[!UICONTROL 儲存]**，Experience PlatformSDK會在Places服務中搜尋您選取之資料庫中的POI。 當您建置應用程式時，POI資料不會包含在程式庫的下載中，但系統會在執行階段將基於位置的POI子集下載至一般使用者的裝置，並根據使用者的GPS座標進行下載。

1. 完成發佈程式以更新SDK設定。

   如需在Experience Platform Launch中發佈的詳細資訊，請參閱 [發佈](https://docs.adobe.com/content/help/zh-Hant/launch/using/reference/publish/overview.html).

### 設定Places擴充功能 {#configure-places-extension}

![](/help/assets/places-extension.png)

## 將Places擴充功能新增至您的應用程式 {#add-places-to-app}

您可以將Places擴充功能新增至Android和iOS應用程式。 您可以在下方看到將「地點」新增至iOS或Android應用程式的步驟。 Places擴充功能也可用於下列平台。 若要在使用這些平台之一進行開發時將地標新增至您的應用程式，請參閱隨附的連結：

**[Cordova Places外掛程式](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React原生位置外掛程式](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Flutter Places增效模組](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Places外掛程式](https://github.com/adobe/xamarin-acpcore)**


### Android

若要使用Java將Places擴充功能新增至您的應用程式：

1. 使用應用程式的Gradle檔案將Places擴充功能新增至專案。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. 在應用程式的主要活動中匯入Places擴充功能。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

若要使用Objective-C或Swift將Places擴充功能新增至您的應用程式：

1. 新增地標和 [行動核心](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) 資料庫至您的專案。 您需要將下列Pod新增至您的 `Podfile`：

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   或者，如果您沒有使用Cocoapod，您可以手動納入行動核心和Places資料庫(位於 [發行頁面](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) 在Github上。

1. 更新您的Cocoapod：

   ```objective-c
   pod update
   ```

1. 開啟Xcode，然後在AppDelegate類別中匯入Core和Places標頭：

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

### 使用行動核心註冊Places擴充功能 {#register-places-mobile-core}

您需要在Android和iOS中使用Mobile Core註冊Places擴充功能。

#### Android

在您的應用程式的 `OnCreate` 方法註冊Places擴充功能：

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

在您的應用程式的 `application:didFinishLaunchingWithOptions:` 方法，以您的其他SDK註冊呼叫註冊Places擴充功能：

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

### 修改Places成員資格存留時間 {#places-ttl}

位置資料可能會很快過時，尤其是當裝置未收到背景位置更新時。

透過設定「 」，控制裝置上Places成員資格資料的存留時間。 `places.membershipttl` 組態設定。 傳入的值代表Places狀態對裝置保持有效的秒數。

#### Android

回呼的內 `MobileCore.start()` 在呼叫之前使用必要的變更更新設定 `lifecycleStart`：

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

在回呼的第一行 `ACPCore`的 `start:` 方法，呼叫 `updateConfiguration:`

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

## 組態金鑰

若要在執行階段以程式設計方式更新SDK設定，請使用下列資訊來變更Places擴充功能設定值。 如需詳細資訊，請參閱 [設定API參考](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| 代碼 | 必填 | 說明 |
| :--- | :--- | :--- |
| `places.libraries` | 是 | 行動應用程式的Places擴充功能程式庫。 它會指定程式庫ID和行動應用程式支援的程式庫名稱。 |
| `places.endpoint` | 是 | 預設Places查詢服務端點，用於取得資料庫和POI的相關資訊。 |
| `places.membershipttl` | 無 | 預設值為3600 （一小時內的秒數）。 表示裝置的Places成員資格資訊將維持有效的時間（以秒為單位）。 |
