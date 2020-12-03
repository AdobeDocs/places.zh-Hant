---
title: 使用您自己的螢幕
description: 您也可以使用Places Service擴充功能API，使用您的監控服務並與Places Service整合。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---


# 使用您自己的螢幕 {#using-your-monitor}

您也可以使用Places擴充功能API，使用您的監控服務並與Places服務整合。

## 註冊地理柵欄

如果您決定使用監控服務，請完成下列步驟，在您目前的位置註冊POI的地理位置：

### iOS

在iOS中，完成下列步驟：

1. 將從iOS的核心位置服務取得的位置更新傳遞至Places擴充功能。

1. 使用 `getNearbyPointsOfInterest` Places擴充功能API取得目前位 `ACPPlacesPoi` 置周圍的物件陣列。

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. 從獲取的對象中提取信 `ACPPlacesPOI` 息，並開始監控這些POI。

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. 將從Google Play服務或Android位置服務取得的位置更新傳遞至Places延伸功能。

1. 使用 `getNearbyPointsOfInterest` Places Extension API取得目前位置 `PlacesPoi` 周圍的物件清單。

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. 從所獲取的物件擷取資 `PlacesPOI` 料，並開始監控這些POI。

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


呼叫 `getNearbyPointsOfInterest` API會產生網路呼叫，以取得目前位置周圍的位置。

>[!IMPORTANT]
>
>您應謹慎呼叫API，或僅在使用者位置發生重大變更時才呼叫API。

## 張貼地理科學事件

### iOS

在iOS中，呼叫委 `processGeofenceEvent` 派中的Places API `CLLocationManager` 。 此API會通知您使用者是否已進入或退出特定地區。

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

在Android中，請呼叫方 `processGeofence` 法，以及Geofence廣播接收器中的適當轉場事件。 您可能想要組織收到的地理柵欄清單，以防止重複登入／退出。

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
