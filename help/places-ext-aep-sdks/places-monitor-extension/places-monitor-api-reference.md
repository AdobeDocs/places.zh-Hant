---
title: Places Monitor API參考
description: Places Monitor的API清單。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 2%

---


# Places Monitor API參考 {#places-api-reference}

## Register Places Monitor Extension

向核心事件中心註冊Places Monitor擴展。

### RegisterExtension(Android)

以下是此API的語法和范常式式碼：

#### 語法

以下是Java語法：

```java
public static void registerExtension();
```

#### 範例

在初始化Experience Platform SDK `onCreate` 其餘部分的方法中呼叫此方法。

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension(iOS)

以下是此API的語法和范常式式碼：

#### 語法

以下是Objective-C中的語法：

```objective-c
+ (void) registerExtension;
```

#### 範例

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## 擴充功能版本

傳回Places Monitor擴充功能的目前版本

### ExtensionVersion(Android)

以下是此API的語法和范常式式碼：

#### 語法

```java
public static String extensionVersion();
```

#### 範例

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion(iOS)

以下是此API的語法和范常式式碼：

#### 語法

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### 範例

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## 啟動設備監控

開始追蹤裝置的位置並監控附近的地點。

### 開始(Android)

如果使用者尚未授與使用裝置位置的授權，對 `start` API的第一次呼叫會提示使用者取得權限。

以下是此API的語法和范常式式碼：

#### 語法

```java
public static void start();
```

#### 範例

```java
PlacesMonitor.start();
```

### 開始(iOS)

>[!IMPORTANT]
>
>要開始監視，位置服務必須具有必要的授權：
>
>* 如果尚未向應用程式提供Places服務的授權， `start` API的第一次呼叫會要求授權使用為應用程式設定的Places服務。
>* 根據您裝置的功能，如果已提供授權，「位置監視器」會根據目前設定來追蹤使用者的位置 `ACPPlacesMonitorMode`。 依預設，螢幕會使用 `ACPPlacesMonitorModeSignificantChanges`。


>[!CAUTION]
>
>如果您在SDK完成初始化之前呼叫開始監控，則可能會忽略此呼叫。

您可從提供給的回呼呼叫，以確 `start` 保SDK已完成初始化 `ACPCore::start:`。

以下是此API的語法和范常式式碼：

#### 語法

```objectivec
+ (void) start;
```

#### 範例

在SDK初始化時啟動「位置監視器」:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

稍後在應用程式執行中啟動Places Monitor:

```objective-c
[ACPPlacesMonitor start];
```

## 停止設備監視

停止追蹤裝置的位置。

### 停止(Android)

以下是此API的語法和范常式式碼：

#### 語法

```java
public static void stop();
```

#### 範例

```java
PlacesMonitor.stop();
```

### 停止(iOS)

以下是此API的語法和范常式式碼：

#### 語法

```objectivec
+ (void) stop;
```

#### 範例

```objective-c
[ACPPlacesMonitor stop];
```

## 更新位置

使用此API可立即更新裝置位置。 當您呼叫此API時，裝置會嘗試依您指定的精確度來判斷位置。 此程式也會重新整理由擴充功能監控的附近POI。

### UpdateLocation(Android)

以下是此API的語法和范常式式碼：

#### 語法

```java
public static void updateLocation();
```

#### 範例

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow(iOS)

#### 語法

```objective-c
+ (void) updateLocationNow;
```

#### 範例

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## 應用程式位置權限

您可以使用此API來設定使用者收到提示並授權用於Places服務的位置權限類型。

### SetLocationPermission(Android)

此API會設定使用者被提示選取的位置權限要求類型。

>[!TIP]
>
>此API僅適用於Android 10及以上版本的裝置。
>
>若要設定要向使用者顯示的適當授權提示，請在前呼叫此API `PlacesMonitor.start()`。 呼叫此方法時，主動監控時，會將位置權限層級升級至要求的權限值。 如果應用程式使用者已提供或拒絕所要求的授權層級，或您嘗試將權限從降級為 `ALWAYS_ALLOW` , `WHILE_USING_APP`則此方法無效。

位置權限可設為下列值之一：

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   此值僅在使用應用程式時提示使用者存取裝置位置。 當使用者在裝置螢幕上檢視應用程式時，例如前景中正在執行活動時，應用程式即視為在使用中。

   >[!TIP]
   >
   >請確定應用程式的資訊清單檔案中已設定ACCESS_FINE_LOCATION使用者權限。

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   此值會提示使用者存取裝置位置，即使應用程式是背景接地亦然。

   >[!TIP]
   >
   >請確定ACCESS_BACKGROUND_LOCATION和ACCESS_FINE_LOCATION使用者權限已設定在應用程式的資訊清單檔案中。

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` 是預設位置權限值。

>[!IMPORTANT]
>
>如果應用程式使用者已獲 `WHILE_USING_APP` 得權限，地理柵欄將不會在作業系統中註冊。 因此，Places Monitor擴充功能不會在背景發生的地區觸發進入／退出事件。

以下是此API的語法和范常式式碼：

#### 語法

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### 範例

要請求權 `WHILE_USING_APP` 限：

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

若要升級至 `ALWAYS_ALLOW` 權限：

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel(iOS)

此API會設定要提示使用者的位置授權要求類型。

要設定向用戶顯示的適當授權提示，請在呼叫前 `SetRequestAuthorizationLevel` 呼叫 `[ACPPlacesMonitor start]`。 若要設定要向使用者顯示的適當授權提示，請在前呼叫此API `[ACPPlacesMonitor start]`。 主動監控時呼叫此方法會將位置授權等級升級至要求的授權值。 如果所請求的授權等級已由應用程式使用者提供或拒絕，或當權限從授權降級至授權時， `ACPPlacesRequestAuthorizationLevelAlways``ACPPlacesRequestAuthorizationLevelWhenInUse` 此方法將無效。

授權級別可以設定為以下值之一：

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   在應用程式使用中，要求使用者使用Places Service的權限。 使用者提示會包含應用程式Info. `NSLocationWhenInUseUsageDescription` plist檔案中索引鍵的文字，而呼叫此方法時，需要有該索引鍵。 如需詳細資訊，請參 [閱requestWhenInUseAuthorization的Apple檔案](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization)。

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   使用此列舉即使應用程式在背景，也可以要求Places服務。 您必須在應 `NSLocationAlwaysUsageDescription` 用程 `NSLocationWhenInUseUsageDescription` 式的Info.plist中擁有和金鑰。 這些鍵定義了在用戶提示期間將顯示的文本。 如需詳細資訊，請參閱 [requestAlwaysAuthorization的Apple檔案](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization)。

`ACPPlacesRequestAuthorizationLevelAlways` 是預設的請求授權值。

>[!IMPORTANT]
>
>授權使用權限的應用程 `ACPPlacesRequestAuthorizationLevelWhenInUse` 式不會在背景發生的地區觸發進入／退出事件。

以下是此API的語法和范常式式碼：

#### 語法

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### 範例

要請求權 `ACPPlacesRequestAuthorizationLevelWhenInUse` 限：

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

若要升級至授 `ACPPlacesRequestAuthorizationLevelAlways` 權：

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## 監控模式（僅限iOS）

監視可設定為以下值之一：

* `ACPPlacesMonitorModeContinuous`

   監控擴展更頻繁地接收和處理位置。 該監控策略耗電大，但精度較高。 如需詳細資訊，請參 [閱Apple持續監控檔案](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)。

* `ACPPlacesMonitorModeSignificantChanges`

   監視擴展僅在設備已經移動了與先前處理的位置相距的顯著距離之後接收並處理位置更新。 該監控策略比連續監控策略耗電少。 如需詳細資訊，請參閱 [Apple重要監控檔案](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode(iOS)

以下是此API的語法和范常式式碼：

#### 語法

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### 範例

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
