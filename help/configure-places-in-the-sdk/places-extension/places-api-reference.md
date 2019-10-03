---
title: Places API reference
seo-title: Places API reference
description: Information about the API references in Places.
seo-description: Information about the API references in Places.
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
          // Call Adobe Places API to process information
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
        // Call Adobe Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Retrieve nearby points of interest

Returns an ordered list of nearby POIs in a callback.

### GetNearbyPointsOfInterest (Android)

Here is the syntax for this method:

**Syntax**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**Example**

Here is the code sample for this method:

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetNearbyPointsOfInterest (iOS)

**Syntax**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**Example**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
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
