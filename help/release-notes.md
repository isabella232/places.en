---
title: Release notes
description: Release notes for Places Service.
---

# Release notes {#release-notes}

## January 9, 2020

* **ACPPlaces 1.4.0**

  * **Android**

    * Added a new API, `setAuthorizationStatus`, to set the device authorization status for Places Services. The value is stored and used in the Places shared state.


## December 3, 2019

* **ACPPlaces 1.3.0**

  * **iOS**

    * Added a new API, `setAuthorizationStatus`, to set the device authorization status for Places Services. The value is stored and used in the Places shared state.

## November 22, 2019

* **PlacesMonitor 2.1.1**

  * **Android**

    * The Monitor now recognizes the boot of an Android device and, if required, registers the geofences again with the OS based on the device's current location.
    * Fixed a race condition that sometimes caused entry/exit events to be discarded.

## October 9, 2019

* **PlacesMonitor 2.1.0**

  * **iOS**

    * Added a new API, `setRequestAuthorizationLevel`, to set the type of location authorization request for which the user will be prompted.


  * **Android**

    * Added a new API, `setLocationPermission`, to set the type of location permission request for which the user will be prompted.
    * The Places Monitor now supports Android 10.

## Aug 8, 2019

The following updates were made in this release:

### UI Updates

Here is a list of the updates to the Places UI:

#### New Features

* Added a new list view that shows POIs without the map.
* Added POI filtering options for the city, the state, the country, and the metadata.
* The first library in an organization is automatically created.
* Added POI sorting to the List View.

#### UI Updates

* Moved the list and details panel to right side of UI.
* Added a new search panel to the top of the UI.
* If only one library is present, this library is automatically selected when you create a POI.
* Moved library management into a popup window.
* Added a POI count next to the filters.

## Aug 6, 2019

The following updates were made in this release:

### Monitor Launch Extension 2.0.0

* Updated the Android and iOS installation instructions for the Places Monitor 2.0.

## July 31, 2019

The following updates were made in this release:

### Places Monitor 2.0.0

* Monitoring status is now persisted between launches.
* The handling of the callback, which resulted from a location permission request no longer requires you to extend PlacesActivity.
* Changed an existing API, allowing developers to clear all Places data from the device:

     Old API: `public static void stop();`

     New API: `public static void stop (final boolean clearData);`

* Updated the use of the `getNearbyPointsOfInterest` API to handle error scenarios more effectively.

## July 25, 2019

The following updates were made in this release:

### ACPPlacesMonitor 2.0.0

* To clear all Places data from the device,

  in ACPPlacesMonitor, replaced an existing API `+ (void) stop;` with`+ (void) stop: (BOOL) clearData;`.

* Updated the use of the ACPPlaces `getNearbyPointsOfInterest` API to handle error scenarios more effectively.

## July 22, 2019

The following updates were made in this release:

### Android Places 1.3.0

* Added a new API that clears out all Places-related data from shared state, in-app memory, and Shared Preference.
* Fixed an issue where shared state was not getting updated during application start.
* Fixed a bug where `getNearbyPointsOfInterest` callback was returning error code `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` on no internet.
* `getNearbyPointsOfInterest` API (without the errorCallback) will have the `successCallback` called with empty poi list, in case of error retrieving the nearby points of interest.

## July 19, 2019

The following updates were made in this release:

**iOS Places 1.2.0**

Added a new API that clears out all Places-related data from shared state, in-app memory, and `NSUserDefaults`.

## June 25, 2019

The following updates were made in this release:

**iOS Places Monitor 1.0.2**

* Quality of life improvements, including better in-code documentation and logging.

## June 17, 2019

The following updates were made in this release:

**iOS Places 1.1.0**

* Added a new API to return an error code when there is a failure retrieving nearby places.
* When privacy status changes to opt-out, all Places-related data will now be wiped from the device.
* Fixed an issue that, after a first launch, sometimes caused Places events to be lost due to bad network conditions.
* Fixed an issue where, when processing POI entry events in quick succession, token replacement via Rules Engine sometimes reference the incorrect POI.

## May 30, 2019 (Places)

**Android Places Monitor 1.0.1**

* Fixed an issue that prevented an entry event for POIs when the Places monitoring is started.

## May 28, 2019

Fixed the following issues in the Places UI:

* Updated the Solution Switcher in Places to align with the rest of the Experience Cloud.
* Fixed an issue where rank was saving in instances where no rank changes were made.
* Increased the minimum allowed radius in the UI to 10 meters.
* Fixed an issue where, if you delete all the numbers in the field, the radius field reset back to 20 meters.

## May 17, 2019 (Places)

The following updates were made in this release:

**Android Places 1.2.0**

* Added a new API to process an individual Geofence.
* Bug fix to prevent multiple consecutive entry events.

**Android Places Monitor 1.0.0**

Initial release of the Places Monitor for Android.

The Places Monitor manages the OS-level Location APIs and communicates directly with the Places extension. With both extensions installed, customers can have out-of-the-box region monitoring in their application.
For more information about the Places Monitor, click here.


## May 2, 2019

**Android Places 1.1.0**

* Introduced a new API for getNearByPlaces, which has an errorCallback and is called with an errorCode that indicates the reason for the error.
* The Places extension now queues the events until a configuration is obtained.
* Added support for environment-aware configurations.
* Bug Fix : corrected the keys for the region entry/exit events
* Storage of last known location now properly respects the user's privacy status


## April 9, 2019

The following updates were made in this release:

**iOS Places Monitor 1.0.1**

* Added full unit test coverage.
* CI integration (CircleCI)
* Code coverage integration (codecov)

## March 25, 2019

iOS Places Monitor 1.0.0

Initial release of the Places Monitor for iOS.

The Places Monitor manages the OS-level Location APIs and communicates directly with the Places extension. With both extensions installed, customers can have out-of-the-box region monitoring in their application. For more information about the Places Monitor, see [Places Monitor extension](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## February 28, 2019

### Beta Release

This is the first release of Places, a set of tools that allows customers to enrich their users' experiences with real world location data. For the first release, our primary use case is to enable mobile apps to retrieve custom location data and act on that data through Adobe Experience Platform Launch.

### Key features

Here are the key features in this release:

#### Places Service UI

We have released a management UI where you can view and manage your points of interest (POIs). You also can organize your POIs into libraries. In addition to standard metadata such as city, state, and category, we also support the ability to add custom metadata to your POIs.

* To see the UI, go to [https://places.adobe.com](https://places.adobe.com).
* To get started with the UI, see [Getting started](/help/getting-started.md).

#### Places Extension

Using the Places Extension, you can add your Places libraries to your mobile app and act on their POIs. Using the rule builder in Experience Platform Launch, you can trigger actions to fire when users enter and exit POIs.

In the Places extension:

* You can choose which POI libraries to include on your app.
* Rule events that trigger on POI entry or exit.
* Create data elements that point to the user's current POI.

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places APIs

You can use the Places APIs to do the following:

* Allow developers to populate and update their list of POIs.
* Build your own UI or integrate with an existing POI database.
* Use the Places API batch endpoints to do a bulk import of POIs.

    You can use the provided Python utility to complete the bulk import.

For more information about the Places APIs, see [Web service API](/help/web-service-api/places-web-services.md).

### Coming Soon

#### Analytics Integration

The Analytics extension is being updated to automatically add location context data from your Places database to all outgoing Analytics calls when a user is within a POI (Passive calls). This update will also allow rule creation to fire Analytics track calls directly at POI entry or exit (Active calls).
