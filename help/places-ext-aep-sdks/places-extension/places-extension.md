---
title: Places 擴充功能
description: 「位置」(Places)擴展允許您根據用戶的位置執行操作。
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: 795808b38851d5afcedc03f58e9a1d6342830934
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Places 擴充功能 {#places-extension}

「位置」(Places)擴展允許您根據用戶的位置執行操作。 此擴展是到Places Query Service API的介面。 通過偵聽包含GPS坐標和地理區域事件的事件，此擴展派發由規則引擎處理的新事件。 「位置」擴展還檢索並提供從API檢索的應用資料的最近POI的清單。 由API返回的區域被儲存在快取和持久性中，這允許有限的離線處理。

## 在Adobe Experience Platform Launch安裝Places擴展

1. 在Experience Platform Launch中，按一下 **[!UICONTROL 擴展]** 頁籤。
1. 在 **[!UICONTROL 目錄]** 頁籤 **[!UICONTROL 位置]** 擴展，然後按一下 **[!UICONTROL 安裝]**。
1. 選擇要在此屬性中使用的「位置」庫。 這些庫將可在您的應用中訪問。
1. 按一下「**[!UICONTROL 儲存]**」。

   按一下 **[!UICONTROL 保存]**,Experience PlatformSDK將在所選庫中搜索Places Services中的POI。 在您構建應用時，POI資料不包括在庫的下載中，但基於位置的POI子集在運行時下載到最終用戶的設備並基於用戶的GPS坐標。

1. 完成發佈過程以更新SDK配置。

   有關在Experience Platform Launch中發佈的詳細資訊，請參見 [發佈](https://docs.adobe.com/content/help/zh-Hant/launch/using/reference/publish/overview.html)。

### 配置「位置」擴展 {#configure-places-extension}

![](/help/assets/places-extension.png)

## 將「位置」擴展添加到應用 {#add-places-to-app}

你可以將「位置」擴展添加到你的Android和iOS應用。 在下面可以看到向iOS或Android應用程式添加位置的步驟。 下面的平台也提供位置擴展。 有關在使用以下平台開發時向應用程式添加位置的資訊，請參閱隨附的連結：

**[Cordova Places插件](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React本地位置插件](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[顫振位置插件](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Places插件](https://github.com/adobe/xamarin-acpcore)**


### Android

要使用Java將「位置」擴展添加到您的應用：

1. 使用應用程式的格式檔案將「位置」擴展添加到項目。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. 在應用程式的主活動中導入「位置」擴展。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

要使用Objective-C或Swift將「位置」擴展添加到您的應用：

1. 添加位置和 [Mobile核心](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) 庫。 您需要將以下Pod添加到 `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   或者，如果您不使用Cocoapods，則可以手動包括我們的Mobile核心和Places庫 [發佈頁](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) 在吉圖布。

1. 更新Cocoapod:

   ```objective-c
   pod update
   ```

1. 開啟Xcode，在AppDelegate類中，導入「核心」和「位置」標題：

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

### 向Mobile核心註冊位置擴展 {#register-places-mobile-core}

您需要在Android和iOS的MobileCore中註冊Places擴展。

#### 安卓

在應用中 `OnCreate` 方法註冊Places擴展：

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

在應用中 `application:didFinishLaunchingWithOptions:` 方法，將Places擴展註冊到其他SDK註冊調用：

**目標 — C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**斯威夫特**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### 修改位置成員資格的生存時間 {#places-ttl}

位置資料可以快速變得陳舊，特別是當設備沒有接收後台位置更新時。

通過設定 `places.membershipttl` 配置設定。 傳入的值表示「放置」狀態對設備保持有效的秒數。

#### 安卓

回叫內 `MobileCore.start()` 在調用前使用必要更改更新配置 `lifecycleStart`:

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

在回調的第一行 `ACPCore``s `start:` 方法，呼叫 `updateConfiguration:`

**目標 — C**

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

**斯威夫特**

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

要在運行時以寫程式方式更新SDK配置，請使用以下資訊更改「放置」擴展配置值。 有關詳細資訊，請參見 [配置API參考](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| 代碼 | 必填 | 說明 |
| :--- | :--- | :--- |
| `places.libraries` | 是 | 移動應用的Places擴展庫。 它指定移動應用支援的庫ID和庫名稱。 |
| `places.endpoint` | 是 | 預設的「放置查詢服務」終結點，用於獲取有關庫和POI的資訊。 |
| `places.membershipttl` | 無 | 預設值為3600（以一小時為單位）。 指示設備的「放置」成員資格資訊將保持有效的時間（秒）。 |
