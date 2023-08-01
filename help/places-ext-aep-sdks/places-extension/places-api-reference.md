---
title: Places API參考
description: Places中API參考的相關資訊。
feature: Mobile SDK
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Places API參考 {#places-api-reference}

以下是Places擴充功能中API參考的相關資訊：

## 處理區域事件

當裝置越過應用程式預先定義的Places Service區域邊界之一時，區域和事件型別就會傳遞至SDK進行處理。

### 程式地理圍欄(Android)

處理a `Geofence` 提供的區域事件 `transitionType`.

傳遞 `transitionType` 從 `GeofencingEvent.getGeofenceTransition()`. 目前 `Geofence.GEOFENCE_TRANSITION_ENTER` 和 `Geofence.GEOFENCE_TRANSITION_EXIT` 支援。

**語法**

此方法的語法如下：

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**範例**

在您的中呼叫此方法 `IntentService` 註冊接收Android地理圍欄事件的網站。

此方法的程式碼範例如下：

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

此方法應在下列位置呼叫： `CLLocationManager` 委派，告知使用者是否已進入或離開特定區域。

**語法**

此方法的語法如下：

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**範例**

此方法的程式碼範例如下：


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofencingEvent (Android)

全部處理 `Geofences` 在 `GeofencingEvent` 同時。

**語法**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**範例**

在您的中呼叫此方法 `IntentService` 已註冊接收Android地理圍欄事件的使用者

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## 擷取附近的地標

傳回回回回撥中附近POI的排序清單。 如果產生的網路呼叫發生錯誤，此方法的多載版本會傳回錯誤碼。

### GetNeartherPointsOfInterest (Android)

此方法的語法如下：

**語法**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**範例**

此方法的程式碼範例如下：

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNeartherPointsOfInterest (iOS)

**語法**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**範例**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## 擷取目前裝置地標

要求裝置目前已知所在的POI清單，並在回撥中傳回。

### GetCurrentPointsOfInterest (Android)

此方法的語法如下：

**語法**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**範例**

此方法的程式碼範例如下：

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**語法**

此方法的語法如下：

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**範例**

此方法的程式碼範例如下：

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## 取得裝置的位置

要求Places擴充功能先前所知之裝置的位置。

>[!TIP]
>
>Places擴充功能只知道透過呼叫提供給它的位置 `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

**語法**

此方法的語法如下：

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**範例**

此方法的程式碼範例如下：

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**語法**

此方法的語法如下：

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**範例**

此方法的程式碼範例如下：

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## 清除使用者端資料


### 清除(Android)

清除Places擴充功能在共用狀態、本機儲存和記憶體中的使用者端資料。

**語法**

此方法的語法如下：

```java
public static void clear();
```

**範例**

此方法的程式碼範例如下：

```java
Places.clear();
```

### 清除(iOS)

清除Places擴充功能在共用狀態、本機儲存和記憶體中的使用者端資料。

**語法**

此方法的語法如下：

```objectivec
+ (void) clear;
```

**範例**

此方法的程式碼範例如下：

```objectivec
[ACPPlaces clear];
```

## 設定位置授權狀態

### setAuthorizationStatus (Android)

*從Places v1.4.0開始提供*

在Places擴充功能中設定授權狀態。

提供的狀態會儲存在Places共用狀態，僅供參考。
呼叫此方法不會影響此裝置的實際位置授權狀態。

**語法**

此方法的語法如下：

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**範例**

此方法的程式碼範例如下：

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*從ACPPlaces v1.3.0開始提供*

在Places擴充功能中設定授權狀態。

提供的狀態會儲存在Places共用狀態，僅供參考。
呼叫此方法不會影響此裝置的實際位置授權狀態。

當裝置授權狀態變更時， `locationManager:didChangeAuthorizationStatus:` 您的方法 `CLLocationManagerDelegate` 叫用的是。 您應從此方法內傳遞新的 `CLAuthorizationStatus` acplaces的值 `setAuthorizationStatus:` API。

**語法**

此方法的語法如下：

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**範例**

此方法的程式碼範例如下：

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
