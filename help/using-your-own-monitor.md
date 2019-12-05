---
title: Using your own monitor
description: You can also use your monitoring services and integrate with Places by using the Places extension APIs.
---

# Using your own monitor {#using-your-monitor}

You can also use your monitoring services and integrate with Places by using the Places extension APIs.

## Registering Geofences

If you decide to use your monitoring services, register the geofences of the POIs around your current location by completing the following steps:

### iOS

In iOS, complete the following steps:

1. Pass the location updates that were obtained from the Core location services of the iOS to the Places extension.

1. Use the `getNearbyPointsOfInterest` Places extension API to get the array of `ACPPlacesPoi` objects around the current location.

    ```objective-c
    - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
        [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
            [self startMonitoringGeoFences:nearbyPoi];
        }];
    }
    ```

1. Extract the information from the obtained `ACPPlacesPOI` objects and start monitoring those POIs.

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

1. Pass the location updates that were obtained from the Google Play services or the Android location services to the Places Extension.

1. Use the `getNearbyPointsOfInterest` Places Extension API to get the list of `PlacesPoi` objects around the current location.

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

1. Extract the data from the obtained `PlacesPOI` objects and start monitoring those POIs.

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


Calling the `getNearbyPointsOfInterest` API results in a network call that gets the location around the current location.

>[!IMPORTANT]
>
>You should call the API sparingly or only when there is significant location change of the user.

## Posting Geofence Events

### iOS

In iOS, call the `processGeofenceEvent` Places API in the `CLLocationManager` delegate. This API notifies you whether the user has entered or exited a specific region.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

In Android, call the `processGeofence` method along with the appropriate transition event in your Geofence broadcast receiver. You may want to curate the list of geofences received to prevent duplicate entries/exits.

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
