---
title: 使用Places Monitor擴充功能
description: 有關如何安裝、配置和使用Places Monitor擴展的資訊。
translation-type: tm+mt
source-git-commit: 7fdaace59886225b7fd9b0eba8cc6c2a139fa2d7
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 6%

---


# 使用Places Monitor擴充功能 {#using-places-monitor-extension}

要使用Places Monitor擴展，請完成以下任務：

## 在Experience Platform Launch中安裝Places Monitor擴充功能

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. 在標籤 **[!UICONTROL Catalog]** 上，找到擴充 **[!UICONTROL Places Monitor]** 功能，然後按一下 **安裝**。
1. 按一下「**[!UICONTROL Save]**」。
1. 依照發佈程式更新SDK組態。

### 配置Places Monitor擴展 {#configure-places-monitor-extension}

Places Monitor副檔名沒有配置任務。

![配置Places Monitor](/help/assets/configure_places_monitor.png)‌

## 將Places Monitor擴充功能新增至您的應用程式 {#add-monitor-extension-to-app}

以下說明如何將Places Monitor擴充功能新增至Android或iOS應用程式。

Places Monitor擴充功能的其他平台支援包括：
**[Cordova Places Monitor](https://github.com/adobe/cordova-acpplaces-monitor/blob/master/README.md)**

**[React Native Places Monitor](https://github.com/adobe/react-native-acpplaces-monitor/blob/master/README.md)**

**[顫振位置監視器](https://github.com/adobe/flutter_acpplaces_monitor/blob/master/README.md)**


### Android

在Android中，完成下列步驟：

#### Java

1. 使用應用程式的Gradle檔案，將Places Monitor擴充功能和Places擴充功能新增至您的專案。

1. 此外，在Gradle檔案中也包含最新的Google位置服務。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. 在應用程式的主要活動中匯入Places Monitor擴充功能。

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

在iOS中，完成下列步驟：

1. Add the library to your project via your Cocoapods `Podfile` by adding `pod 'ACPPlacesMonitor'`.
1. 匯入「位置」和「位置」監控程式庫：

#### Objective-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## 註冊並啟動Places Monitor {#register-start-places-monitor}

您必須註冊並啟動Android或iOS中的Places Monitor。

## Android

在Android中，完成下列步驟：

### Java

在您應用程式的方法中， `OnCreate` 註冊Places Monitor擴充功能：

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
            PlacesMonitor.start();//Start monitoring the geo-fences
        } catch (Exception e) {
            //Log the exception
        }
    }
}
```

>[!IMPORTANT]
>
>位置監控取決於位置擴展。 手動安裝「Places 監視」擴充功能時，請確定您也將 `places.aar` 資料庫新增至專案。

## iOS

在iOS應用程式中`application:didFinishLaunchingWithOptions`，註冊 `PlacesMonitor` 並放置行動核心：

### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>位置監控取決於位置擴展。 When manually installing the Places Monitor extension, ensure that you also add the `libACPPlaces_iOS.a` library to your project.


## 新增權限至資訊清單

### Android

**Java**

對於所有Android版本，若要宣告您的應用程式需要位置權限，請在應用程式資訊清單中新增元素，作為頂層元素的子項 `<uses-permission>``<manifest>` 。 針對以API等級29及更高版本為目標的Android應用程式，若要允許應用程式存取背景中的位置，請加入ACCESS_BACKGROUND_LOCATION權限。

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## 在背景啟用位置更新  {#enable-location-updates-background}

iOS支援將位置事件傳送至已暫停或不再執行的應用程式。 若要在背景接收Places Monitor擴充功能的位置更新，請在中設定您應用程式的位置更新功能 `Xcode.background-location-updates`。

![使用Places Monitor](/help/assets/using-the-places-monitor_1.png)

## 配置plist鍵

您的應用程式檔案中必須包含下列金 `Info.plist` 鑰：

* `NSLocationWhenInUseUsageDescription` -文字應說明應用程式在前景執行時，要求存取使用者位置資訊的原因。
* `NSLocationAlwaysAndWhenInUseUsageDescription` -文字應說明應用程式為何會隨時要求存取使用者的位置資訊。

>[!TIP]
>
>如果您的應用程式支援iOS 10及更早版本，則 `NSLocationAlwaysUsageDescription` 也需要金鑰。

![](/help/assets/using-the-places-monitor_2.png)
