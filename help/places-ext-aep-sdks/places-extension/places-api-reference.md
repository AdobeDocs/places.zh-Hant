---
title: Places API參考
seo-title: Places API參考
description: Places中API參考的相關資訊。
seo-description: Places中API參考的相關資訊。
translation-type: tm+mt
source-git-commit: 69173bdbd1a69ae1b75ba70e775a4603d1f1b8fc

---


# Places API參考 {#places-api-reference}

以下是Places中API參考的相關資訊：

## 處理地區事件

當裝置跨越您應用程式中預先定義的「地標」區域邊界時，區域和事件類型會傳遞至SDK以進行處理。

### ProcessGeofence(Android)

處理所 `Geofence` 提供的地區事件 `transitionType`。

傳遞 `transitionType` 自 `GeofencingEvent.getGeofenceTransition()`。 目前 `Geofence.GEOFENCE_TRANSITION_ENTER` 並 `Geofence.GEOFENCE_TRANSITION_EXIT` 受支援。

**語法**

以下是此方法的語法:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**範例**

在已註冊接收Android地 `IntentService` 理序列事件的您中呼叫此方法。

以下是此方法的範例程式碼:

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

### ProcessRegionEvent(iOS)

應在委派中呼叫此方 `CLLocationManager` 法，以告知使用者是否已進入或退出特定地區。

**語法**

以下是此方法的語法:

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**範例**

以下是此方法的範例程式碼:


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofercingEvent(Android)

同時 `Geofences` 處理 `GeofencingEvent` 所有內容。

**語法**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**範例**

在已註冊接收Android地 `IntentService` 理序列事件的您中呼叫此方法

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

傳回回回呼中附近POI的有序清單。 如果導致的網路呼叫發生問題，此方法的過載版本會傳回錯誤碼。

### GetOnnexerPointsOfInterest(Android)

以下是此方法的語法:

**語法**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**範例**

以下是此方法的範例程式碼:

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

### GetOnnexterPointsOfInterest(iOS)

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

## 擷取目前裝置的興趣點

請求設備當前已知位於的POI清單，並在回呼中返回這些POI。

### GetCurrentPointsOfInterest(Android)

以下是此方法的語法:

**語法**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**範例**

以下是此方法的範例程式碼:

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest(iOS)

**語法**

以下是此方法的語法:

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**範例**

以下是此方法的範例程式碼:

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## 取得裝置的位置

請求裝置的位置（如先前所知），由Places擴充功能。

>[!TIP]
>
>「地標」分機只會知道透過呼叫提供給它的位置 `GetNearbyPointsOfInterest`。


### GetLastKnownLocation(Android)

**語法**

以下是此方法的語法:

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**範例**

以下是此方法的範例程式碼:

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation(iOS)

**語法**

以下是此方法的語法:

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**範例**

以下是此方法的範例程式碼:

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## 清除用戶端資料


### 清除(Android)

清除處於共用狀態、本地儲存和記憶體中的「位置」的客戶端資料。

**語法**

以下是此方法的語法:

```java
public static void clear();
```

**範例**

以下是此方法的範例程式碼:

```java
Places.clear();
```

### clear(iOS)

清除處於共用狀態、本地儲存和記憶體中的「位置」的客戶端資料。

**語法**

以下是此方法的語法:

```objectivec
+ (void) clear;
```

**範例**

以下是此方法的範例程式碼:

```objectivec
[ACPPlaces clear];
```
