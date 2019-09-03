---
title: Places Monitor API reference
seo-title: Places Monitor API reference
description: A list of the APIs for the Places Monitor. 
seo-description: A list of the APIs for the Places Monitor.  
---

# Places Monitor API reference {#places-api-reference}

## Register Places Monitor Extension

Registers the Places Monitor extension with the Core Event Hub.

### RegisterExtension (Android)

#### Syntax

Here is the syntax in Java:

```java
public static void registerExtension();
```

#### Example

Call this method in the `onCreate` method where you initialize the rest of the Experience Platform SDK.

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

### RegisterExtension (iOS)

#### Syntax

Here is the syntax in Objective-C:

```objective-c
+ (void) registerExtension;
```

#### Example

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

## Extension version

Returns the current version of the Places Monitor extension

### ExtensionVersion (Android)

#### Syntax

```java
public static String extensionVersion();
```

#### Example

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

#### Syntax

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Example

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Start device monitoring

Begin tracking the device's location and monitoring nearby Places.


### Start (Android)

If authorization to use device location has not been granted by the user, the first call to the `start` API prompts the user for permission.

#### Syntax

```java
public static void start();
```

#### Example

```java
PlacesMonitor.start();
```

### Start (iOS)

>[!IMPORTANT]
>
>To begin monitoring, the location service must have the necessary authorization:
>
>* If the authorization for the location service has not been provided to the application, the first call to the `start` API requests the authorization to use the location service as configured for the application.
>* Depending on your device's capabilities, if the authorization has been provided, the Places Monitor tracks the user's location based on the currently set `ACPPlacesMonitorMode`. By default, the monitor uses `ACPPlacesMonitorModeSignificantChanges`.

>[!CAUTION]
>
>If your call to start monitoring is made before the SDK has finished initializing, it might be ignored.  

You can ensure the SDK has finished initialization by calling `start` from the callback provided to `ACPCore::start:`.


#### Syntax

```objectivec
+ (void) start;
```

#### Example

Starting the Places Monitor when the SDK is initializing:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Starting the Places Monitor later in app execution:

```objective-c
[ACPPlacesMonitor start];
```

## Stop device monitoring

Stops tracking the device's location.

### Stop (Android)

#### Syntax

```java
public static void stop();
```

#### Example

```java
PlacesMonitor.stop();
```

### Stop (iOS)

#### Syntax

```objectivec
+ (void) stop;
```

#### Example

```objective-c
[ACPPlacesMonitor stop];
```

## Update Location

Use this API for an immediate update on the device's location. When you call this API, the device attempts to determine the location with the level of accuracy that you specified. This process also refreshes the nearby POIs that are monitored by the extension.

### UpdateLocation (Android)

#### Syntax

```java
public static void updateLocation();
```

#### Example

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow (iOS)

#### Syntax

```objective-c
+ (void) updateLocationNow;
```

#### Example

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## Monitoring Mode (iOS only)

Monitoring can be set to one of the following values:

* `ACPPlacesMonitorModeContinuous`

  The monitoring extension receives and processes locations more frequently. This monitoring strategy consumes a lot of power but provides higher accuracy. For more information, see [Apple documentation on continuous monitoring](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation).

* `ACPPlacesMonitorModeSignificantChanges`

  The monitoring extension only receives and processes location updates after the device has moved a significant distance from the previously processed location. This monitoring strategy consumes less power than the continuous monitoring strategy. For more information, see [Apple documentation on significant monitoring](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

#### Syntax

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Example

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
