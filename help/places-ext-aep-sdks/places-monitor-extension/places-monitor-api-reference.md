---
title: Places Monitor API reference
description: A list of the APIs for the Places Monitor.
---

# Places Monitor API reference {#places-api-reference}

## Register Places Monitor Extension

Registers the Places Monitor extension with the Core Event Hub.

### RegisterExtension (Android)

Here is the syntax and example code for this API:

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

Here is the syntax and example code for this API:

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

Here is the syntax and example code for this API:

#### Syntax

```java
public static String extensionVersion();
```

#### Example

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Here is the syntax and example code for this API:

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

Here is the syntax and example code for this API:

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
>* If the authorization for the Places Service has not been provided to the application, the first call to the `start` API requests the authorization to use the Places Service as configured for the application.
>* Depending on your device's capabilities, if the authorization has been provided, the Places Monitor tracks the user's location based on the currently set `ACPPlacesMonitorMode`. By default, the monitor uses `ACPPlacesMonitorModeSignificantChanges`.

>[!CAUTION]
>
>If your call to start monitoring is made before the SDK has finished initializing, it might be ignored.  

You can ensure the SDK has finished initialization by calling `start` from the callback provided to `ACPCore::start:`.

Here is the syntax and example code for this API:

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

Here is the syntax and example code for this API:

#### Syntax

```java
public static void stop();
```

#### Example

```java
PlacesMonitor.stop();
```

### Stop (iOS)

Here is the syntax and example code for this API:

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

Here is the syntax and example code for this API:

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

## App Location permission

You can use this API to set the type of location permission that the user is prompted for and authorized to use for Places Service.

### SetLocationPermission (Android)

This API sets the type of location permission request for which the user is prompted to select.

>[!TIP]
>
>This API is effective only for devices that are on Android 10 and above.
>
>To set the appropriate authorization prompt to be displayed to the user, call this API before the `PlacesMonitor.start()`. Calling this method, while actively monitoring, upgrades the location permission level to the requested permission value. If the requested authorization level is either already provided or denied by the application user, or if you attempt to downgrade the permission from `ALWAYS_ALLOW` to `WHILE_USING_APP`, this method has no effect.

Location permission can be set to one of the following values:

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

  This value prompts the user to access device location only while using the application. An app is considered to be in use when the user is looking at the app on their device screen, for example an activity is running in the foreground.

  >[!TIP]
  >
  >Make sure the ACCESS_FINE_LOCATION user permission is set in the app's manifest file.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

  This value prompts the user to access device location even when the application is backgrounded.  

  >[!TIP]
  >
  >Make sure the ACCESS_BACKGROUND_LOCATION and  ACCESS_FINE_LOCATION user permissions are set in the app's manifest file.

  `PlacesMonitorLocationPermission.ALWAYS_ALLOW` is the default location permission value.

>[!IMPORTANT]
>
>If the app user is granted the `WHILE_USING_APP` permission, geofences will not be registered with the operating system. As a result, the Places Monitor extension will not trigger entry/exit events on regions that are happening in the background.

Here is the syntax and example code for this API:

#### Syntax

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Example

To request the `WHILE_USING_APP` permission:

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

To upgrade to `ALWAYS_ALLOW` permission:

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

This API sets the type of location authorization request for which the user will be prompted.

To set the appropriate authorization prompt to be displayed to the user, call `SetRequestAuthorizationLevel` before calling `[ACPPlacesMonitor start]`. To set the appropriate authorization prompt to be shown to the user, call this API before the `[ACPPlacesMonitor start]`. Calling this method while actively monitoring will upgrade the location authorization level to the requested authorization value. If the requested authorization level is either already provided or denied by the application user or when there is a downgrade of permission from `ACPPlacesRequestAuthorizationLevelAlways` to `ACPPlacesRequestAuthorizationLevelWhenInUse` authorization, this method has no effect.

Authorization level can be set to one of the following values:

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

    Requests the user’s permission to use Places Service while the app is in use. The user prompt contains the text from the `NSLocationWhenInUseUsageDescription` key in your app Info.plist file, and the presence of that key is required when calling this method. For more information see the  [Apple documentation on requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

    Use this enum to request Places Service even when the app is in the background. You must have the `NSLocationAlwaysUsageDescription` and `NSLocationWhenInUseUsageDescription` keys in your app’s Info.plist. These keys define the text that will appear during the user prompt. For more information see the [Apple documentation on requestAlwaysAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` is the default request authorization value.

>[!IMPORTANT]
>
>The application that authorized the use of the `ACPPlacesRequestAuthorizationLevelWhenInUse` permission will not trigger entry/exit events on regions that are happening in the background.

Here is the syntax and example code for this API:

#### Syntax

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### Example

To request the `ACPPlacesRequestAuthorizationLevelWhenInUse` permission:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

To upgrade to `ACPPlacesRequestAuthorizationLevelAlways` authorization:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## Monitoring Mode (iOS only)

Monitoring can be set to one of the following values:

* `ACPPlacesMonitorModeContinuous`

    The monitoring extension receives and processes locations more frequently. This monitoring strategy consumes a lot of power but provides higher accuracy. For more information, see [Apple documentation on continuous monitoring](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation).

* `ACPPlacesMonitorModeSignificantChanges`

    The monitoring extension only receives and processes location updates after the device has moved a significant distance from the previously processed location. This monitoring strategy consumes less power than the continuous monitoring strategy. For more information, see [Apple documentation on significant monitoring](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Here is the syntax and example code for this API:

#### Syntax

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Example

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
