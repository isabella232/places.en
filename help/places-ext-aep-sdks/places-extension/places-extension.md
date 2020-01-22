---
title: Places extension
description: The Places extension allows you to act based on the location of your users.
---

# Places extension {#places-extension}

The Places extension allows you to act based on the location of your users. This extension is the interface to the Places Query Service APIs. By listening for events that contain GPS coordinates and geofence region events, this extension dispatches new events that are processed by the Rules Engine. The Places extension also retrieves and delivers a list of the nearest POI for the app data that retrieves from the APIs. The regions returned by the APIs are stored in cache and persistence, which allows limited offline processing.

## Install the Places extension in Adobe Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. On the **[!UICONTROL Catalog]** tab, locate the **[!UICONTROL Places]** extension, and click **[!UICONTROL Install]**.
1. Select the Places libraries you want to use in this property. These are the libraries that will be accessible in your app.
1. Click **[!UICONTROL Save]**. 

    When you click **[!UICONTROL Save]**, the Experience Platform SDK searches the Places Services for POIs in the libraries that you selected. The POI data is not included in the download of the library when you build the app, but a location-based subset of POIs is downloaded to the end user's device at runtime and is based on the user's GPS coordinates.

1. Complete the publishing process to update the SDK configuration.

   For more information about publishing in Experience Platform Launch, see [Publishing](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Configure the Places extension {#configure-places-extension}

  ![](//help/assets/places-extension.png)

## Add the Places extension to your app {#add-places-to-app}

You can add the Places extension to your Android and iOS apps.

### Android

To add the Places extension to your app by using Java:

1. Add the Places extension to your project using your app's gradle file.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Import the Places extension in your application's main activity.

    ```java
    import com.adobe.marketing.mobile.Places;
    ```


### iOS

To add Places extension to your app by using Objective-C or Swift:

1. Add the Places and [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) libraries to your project. You will need to add the following pods to your `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Alternatively, if you are not using Cocoapods, you can manually include the Mobile Core and the Places libraries from our [releases page](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) on Github.

1. Update your Cocoapods:

   ```objective-c
   pod update
   ```

1. Open Xcode, and in your AppDelegate class, import the Core and the Places headers:

    **Objective-C**

    ```objective-c
    #import "ACPCore.h"
    #import "ACPPlaces.h"
    ```

    **Swift**

    ```swift
    import ACPCore
    import ACPPlaces
    ```

### Register the Places extension with Mobile Core {#register-places-mobile-core}

You need to register the Places extension with Mobile Core in Android and iOS.

#### Android

In your App's `OnCreate` method register the Places extensions:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

In your App's `application:didFinishLaunchingWithOptions:` method, register the Places extension with your other SDK registration calls:

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

## Configuration keys

To update the SDK configuration programmatically at runtime, use the following information to change your Places extension configuration values. For more information, see [Configuration API Reference](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Key | Required | Description |
| :--- | :--- | :--- |
| `places.libraries` | Yes | The Places extension libraries for the mobile app. It specifies the library ID and the name of the library that the mobile app supports. |
| `places.endpoint` | Yes | The default Experience Platform Location Query Service endpoint, which is used to get information about libraries and POIs. |

