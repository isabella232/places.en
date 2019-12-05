---
title: Places API reference
description: Information about the API references in Places.
---

# Places API reference {#places-api-reference}

Here is information about the API references in Places:

## Processing a region event

When a device crosses one of your app's pre-defined Places region boundaries, the region and event type are passed to the SDK for processing.

### ProcessGeofence (Android)

Process a `Geofence` region event for the provided `transitionType`.

Pass the `transitionType` from `GeofencingEvent.getGeofenceTransition()`. Currently `Geofence.GEOFENCE_TRANSITION_ENTER` and `Geofence.GEOFENCE_TRANSITION_EXIT` are supported.

**Syntax**

Here is the syntax for this method:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Example**

Call this method in your `IntentService` that is registered for receiving Android geofence events.

Here is a code sample for this method:

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

This method should be called in the `CLLocationManager` delegate, which tells if the user has entered or exited a specific region.

**Syntax**

Here is the syntax for this method:

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**Example**

Here is the code sample for this method:


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofencingEvent (Android)

Process all `Geofences` in the `GeofencingEvent` at the same time.

**Syntax**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Example**

Call this method in your `IntentService` that is registered for receiving Android geofence events

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

## Retrieve nearby points of interest

Returns an ordered list of nearby POIs in a callback. An overloaded version of this method returns an error code if something went wrong with the resulting network call.

### GetNearbyPointsOfInterest (Android)

Here is the syntax for this method:

**Syntax**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**Example**

Here is the code sample for this method:

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

### GetNearbyPointsOfInterest (iOS)

**Syntax**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**Example**

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

## Retrieve current device points of interest

Requests a list of POIs in which the device is currently known to be in and returns them in a callback.

### GetCurrentPointsOfInterest (Android)

Here is the syntax for this method:

**Syntax**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**Example**

Here is the code sample for this method:

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

**Syntax**

Here is the syntax for this method:

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**Example**

Here is the code sample for this method:

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## Get the location of the device

Requests the location of the device, as previously known, by the Places extension.

>[!TIP]
>
>The Places extension only knows about locations that were provided to it via calls to `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

**Syntax**

Here is the syntax for this method:

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**Example**

Here is the code sample for this method:

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

**Syntax**

Here is the syntax for this method:

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**Example**

Here is the code sample for this method:

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## Clear client-side data


### Clear (Android)

Clears out the client-side data for Places in shared state, local storage, and in-memory.

**Syntax**

Here is the syntax for this method:

```java
public static void clear();
```

**Example**

Here is the code sample for this method:

```java
Places.clear();
```

### clear (iOS)

Clears out the client-side data for Places in shared state, local storage, and in-memory.

**Syntax**

Here is the syntax for this method:

```objectivec
+ (void) clear;
```

**Example**

Here is the code sample for this method:

```objectivec
[ACPPlaces clear];
```

## Set location authorization status

### setAuthorizationStatus (Android)

Coming soon

### setAuthorizationStatus (iOS)

*Available starting with ACPPlaces v1.3.0*

Sets the authorization status in the Places extension.

The status provided is stored in the Places shared state, and is for reference only.
Calling this method does not impact the actual location authorization status for this device.

When the device authorization status changes, the `locationManager:didChangeAuthorizationStatus:` method of your `CLLocationManagerDelegate` is invoked. From within this method, you should pass the new `CLAuthorizationStatus` value to the ACPPlaces `setAuthorizationStatus:` API.

**Syntax**

Here is the syntax for this method:

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**Example**

Here is the code sample for this method:

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
