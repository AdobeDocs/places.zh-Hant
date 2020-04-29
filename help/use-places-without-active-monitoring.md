---
title: 不使用活動區域監控的地點服務
description: 本節提供如何使用Places Service而不進行作用中地區監控的資訊。
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9

---


# 不使用活動區域監控的地點服務 {#use-places-without-active-monitoring}

您應用程式的使用案例可能不需要主動監視區域。 Places Service仍可用來取得使用者的位置資料，並與其他Experience Platform產品整合。

## 先決條件

開發人員將使用目標平台作業系統提供的API來收集裝置位置。

>[!TIP]
>
>如果您應用程式的使用案例需要使用中的地區監控，請參 [閱「使用位置監控擴充功能」](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

要使用「地點服務」而不監視活動區域，請執行以下操作：

## 1.收集使用者的位置

應用程式開發人員必須使用Google Play Services(Android)提 `CoreLocation.framework` 供的(iOS)或 `Location` API來收集裝置的目前位置。

如需詳細資訊，請參閱下列檔案：

- [CoreLocation](https://developer.apple.com/documentation/corelocation) (Apple)
- [Google Play服務中的位置API](https://developer.android.com/training/location) (Google)

## 2.從SDK擷取附近的地標

在您取得使用者位置後，可將它傳遞至SDK，以取得附近POI的清單。

### Android

以下是Android中的範例實作，使用 [`BroadcastReceiver`](https://codelabs.developers.google.com/codelabs/background-location-updates-android-o/index.html?index=..%2F..index#5):

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }
}
```

### Objective-C

以下是iOS的範例實作。 此代碼顯示以下方法 [`locationManager:didUpdateLocations:`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager?language=objc)[`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager?language=objc)的實現：

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}
```

### Swift

以下是iOS的範例實作。 此代碼顯示以下方法 [`locationManager(_:didUpdateLocations:)`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager)[`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager)的實現：

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}
```

## 3.將地標資料附加至Analytics請求

透過呼叫 `getNearbyPointsOfInterest` API,Places SDK將透過Launch中的資料元素，提供與裝置相關的所有POI資料。 使用「附 [加資料](https://aep-sdks.gitbook.io/docs/resources/user-guides/attach-data) 」規則，「置入」資料會自動新增至Analytics的未來請求。 如此，在收集裝置位置時，就不需要對Analytics進行一次性呼叫。

如需 [此主題的詳細資訊，請參閱新增位置內容](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md) 至Analytics請求。

## 可選——當使用者在POI中時觸發參加事件

>[!TIP]
>
>擷取「地標」資料的建議方式是將「地 [標」資料附加至您的Analytics請求](#attach-places-data-to-your-analytics-requests)。
>
>如果使用案例需要 [SDK觸發地區登入事件](places-ext-aep-sdks/places-extension/places-event-ref.md#processregionevent) ，則需要依下列說明手動完成。

API傳回的清單 `getNearbyPointsOfInterest` 包含自 [訂物件](places-ext-aep-sdks/places-extension/cust-places-objects.md) ，指出使用者目前是否在POI中。 如果使用者位於POI中，您可讓SDK觸發該地區的登入事件。

>[!IMPORTANT]
>
>若要防止應用程式在一次瀏覽中觸發多個參加項目事件，請保留您知道使用者已輸入的地區清單。 當處理來自SDK的附近POI的回應時，只有在您的清單中未列出地區時，才會觸發登入事件。
>
>在下列程式碼范 `NSUserDefaults` 例中，(iOS)和 `SharedPreferences` (Android)用於管理地區清單：

### Android

下列程式碼範例顯示回呼中提供之結果的處 `getNearbyPointsOfInterest`理方式 `List<PlacesPOI>`:

```java
void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
    // get the list of regions we know the user is already within from SharedPreferences
    SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
    Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

    // loop through new placesPOIS and post entry events for pois that aren't already in our list
    // also create the new list of regions that the user is in
    Set<String> updatedRegionsUserIsIn = new HashSet<String>();
    for (PlacesPOI poi : nearbyPois) {
        // check if the user is in this poi
        if (poi.containsUser()) {
            // the user is in the poi, now we need to make sure we haven't already recorded this entry event
            if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                Geofence poiGeofence = new Geofence.Builder()
                    .setRequestId(poi.getIdentifier())
                    .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                    .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                    .setExpirationDuration(Geofence.NEVER_EXPIRE)
                    .build();
                Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
            }

            // add the region to our new list of regions
            updatedRegionsUserIsIn.add(poi.getIdentifier());
        }
    }

    // update SharedPreferences with our new list of regions
    SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
    editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
}
```

### Objective-C

下列程式碼範例顯示回呼中提供結果的處 `getNearbyPointsOfInterest:limit:callback:errorCallback:`理方式 `NSArray<ACPPlacesPoi *> *`:

```objectivec
- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

下列程式碼範例顯示回呼中提供結果的處 `getNearbyPoints(_ ofInterest: CLLocation, limit: UInt, callback: (([ACPPlacesPoi]?) -> Void)?, errorCallback: ((ACPPlacesRequestError) -> Void)?)`理方式 `[ACPPlacesPoi]`:

```swift
func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

## 完整的範例實作

以下程式碼範例將示範如何擷取裝置的目前位置、觸發必要的登入事件，並確保一次瀏覽時不會取得相同位置的多個登入項目。

此程式碼範例包含當使 [用者在POI中時觸發參加事件的選用步驟](#trigger-entry-events-when-the-user-is-in-a-poi)。

>[!IMPORTANT]
>
>這些片段只 **是範例** 。 開發人員必須決定要如何實作功能，而決策應考量目標作業系統建議的最佳實務。

### Android

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                    handleUpdatedPOIs(pois);
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }

    void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
        // get the list of regions we know the user is already within from SharedPreferences
        SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
        Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

        // loop through new placesPOIS and post entry events for pois that aren't already in our list
        // also create the new list of regions that the user is in
        Set<String> updatedRegionsUserIsIn = new HashSet<String>();
        for (PlacesPOI poi : nearbyPois) {
            // check if the user is in this poi
            if (poi.containsUser()) {
                // the user is in the poi, now we need to make sure we haven't already recorded this entry event
                if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                    Geofence poiGeofence = new Geofence.Builder()
                        .setRequestId(poi.getIdentifier())
                        .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                        .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                        .setExpirationDuration(Geofence.NEVER_EXPIRE)
                        .build();
                    Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
                }

                // add the region to our new list of regions
                updatedRegionsUserIsIn.add(poi.getIdentifier());
            }
        }

        // update SharedPreferences with our new list of regions
        SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
        editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
    }
}
```


### Objective-C

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
        [self handleUpdatedPOIs:nearbyPoi];
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}

- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
        self.handleUpdatedPOIs(nearbyPoi!)
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}

func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

除了在SDK中觸發Places Service項目事件外，由於觸發項目事件，SDK的其餘成員也可透過Experience Platform Launch使用定義您POI的所 `data elements` 有資料。 有了Experience Platform Launch，您 `rules`就可以將Places Service資料動態附加至SDK處理的傳入事件。 例如，您可以附加使用者所在之POI的中繼資料，並將資料以內容資料的形式傳送至Analytics。

如需詳細資訊，請參 [閱搭配使用Places Service和其他Adobe解決方案](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)。
