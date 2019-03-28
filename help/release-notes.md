---
title: Release notes
seo-title: Release notes for Adobe Location Services.
description: Release notes for Adobe Location Services.
seo-description: Release notes for Adobe Location Services.
---

# Release notes

## February 28, 2019

### Beta Release

This is the first release of Places, a set of tools that allows customers to enrich their users' experiences with real world location data. For the first release, our primary use case is to enable mobile apps to retrieve custom location data and act on that data through Adobe Launch.

### Key features

Here are the key features in this release:

#### Places UI 

We have released a management UI where you can view and manage your points of interest (POIs). You also can organize your POIs into libraries. In addition to standard metadata such as city, state, and category, we also support the ability to add custom metadata to your POIs.

* To see the Places UI, go to [https://places.adobe.com](https://places.adobe.com). 
* To get started with the Places UI, see [Getting Started](/help/getting-started.md).

#### Places Launch Extension

Using the Places Launch Extension, you can add your Places libraries to your mobile app and act on their POIs. Using the rule builder in Launch, you can trigger actions to fire when users enter and exit POIs.

In the Places extension:

* You can choose which POI libraries to include on your app.
* Rule events that trigger on POI entry or exit.
* Create data elements that point to the user's current POI.

For more information about the Places extension, see [Places extension (beta)](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/places-extension-1).

#### Places APIs 

You can use the Places APIs do do the following:

* Allow developers to populate and update their list of POIs. 
* Build your own UI or integrate with an existing POI database. 
* Use the Places API batch endpoints to do a bulk import of POIs. 

    A python utility is provided with the APIs. 

For more information about the Places APIs, see [Places web services](/help/places-rest-apis/places-rest-apis.md).

### Coming Soon

#### Analytics Integration

The Analytics Launch extension is being updated to automatically add location context data from your Places database to all outgoing Analytics calls when a user is within a POI (Passive calls). This update will also allow rule creation to fire Analytics track calls directly at POI entry or exit (Active calls).

