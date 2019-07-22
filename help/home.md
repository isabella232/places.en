---
title: Overview
seo-title: Adobe Experience Platform Location Services overview
description: Experience Platform Location Services is an important context for understanding the engagement of mobile users. By using this context, mobile app developers can enhance the app design and make it a more personalized and engaging experience. 
seo-description: Experience Platform Location Services is an important context for understanding the engagement of mobile users. By using this context, mobile app developers can enhance the app design and make it a more personalized and engaging experience. 
---

# Overview {#home}

Experience Platform Location Services is an important context for understanding the engagement of mobile users. By using this context, mobile app developers can enhance the app design and make it a more personalized and engaging experience. Places is a geo-location service that enables mobile app developers to understand the location context by using rich and easy-to-use SDK interfaces accompanied by a flexible database of points of interests (POIs).

Experience Platform Location Services in Adobe's Experience Cloud geo-location service allows you to achieve the following:

* Create and manage a database of POIs that can be leveraged with other Experience Cloud solutions.
* Attach custom metadata to the POIs to make them richer and more meaningful by specifying additional attributes. 
* Visualize the POIs on a map to easily understand the spatial context and add/edit metadata attributes. 
* Configure the SDK in Adobe Experience Platform Launch to define your location-triggered rules and metadata based conditions.
* Reduce the code that you need to write to a monitor device's location and use Adobe's location monitor to automatically trigger the location-specific rules.

This will allow you to take actions from location signals in real time, when and where it matters. The right context provides a more enriching mobile engagement experience.

Here are some of the ways you can use Experience Platform Location Services: 

* Send a real time notification when someone enters a POI, _"Hey..welcome to the stadium"_. 
* Analyze foot traffic of your own stores versus your competitor stores.
* Segment an audience based on offline behavior by using audience profiles with location context.
* Target a user with an in-store experience when relevant.

## Experience Platform Location Services Components

Experience Platform Location Services comprises the following components:

* **Experience Platform Location Services Web Service** You can create and manage POIs by using the REST APIs. 

  For more information about the REST APIs, see [Places web service](https://placesdocs.com/places-services-by-adobe-documentation/places-rest-apis).
* **Experience Platform Location Services UI** Visualize POIs on a map to understand the spatial context and to add/edit POIs and their custom metadata.
* **Places SDK** The multi-platform mobile API interface to integrate the location context in your mobile apps. 

  For more information about the SDKs, see [Places extension](https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-extension).

* **Places rules** The geo-intelligent Experience Platform Launch rules that enable you to trigger actions with entry and exit events. 

  The rules also allow you to use geo-attributes in conditions to personalize the experience. 

* **Places Monitor**  
  
  The multi-platform mobile SDK which can be embedded in your mobile app to automatically monitor your user's location changes and trigger Places rules. For more information, see [Places extension](https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-extension).

## Terminology

Here are some common terms that are used in the Experience Platform Location Services documentation:

* A **point of interest \(POI\)** is a geo-location that is of interest to your organization.  You can define POIs with attributes such as a name, radius, address, category, and metadata tags.
* A **geofence** is a type of POI.  This POI type is a virtual geographic boundary that is defined by latitude and longitude coordinates.
* A **beacon** is a type of POI.  This POI type is a physical device that represents a location by emitting a low power bluetooth signal. Beacons support is coming in a future release.
* A **library** is a collection of POIs, which are grouped to easily attach rules to a set instead of one POI. 
* A SDK **extension**, is the Experience Platform Launch

   extension that is required to integrate the Places SDK in your mobile apps.   
  The extension used with the other mobile SDKs to add location context to your experiences.

* An **organization** is the Adobe entity that identifies your company in the Adobe Experience Cloud. Typically, an organization is your company name. However, a company can have more than one organization. The organization administrator can configure groups and users and configure single sign-on functionality.
* The **orgID** is the ID that represents your organization across Adobe Experience Platform.   For more information, see [Finding your orgID](https://forums.adobe.com/thread/2339895).
* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. For more information, see [Overview](https://marketing.adobe.com/resources/help/en_US/mcvid/).

## Understanding the Experience Platform Location Services UI

To access the Experience Platform Location Services UI, in a browser, go to  [https://places.adobe.com](https://places.adobe.com) and log in with your Adobe ID. 

Here is some basic information to help you get familiar with the UI:

* In the upper right corner of the screen, there are buttons for zooming in and out, centering on your current location (Find Me), and switching between the map view and satellite view.
* Double click to zoom in or click and drag to recenter the map.
* You can also use the arrow keys to scroll the map
* In the lower right corner, click the New Poi button to create a new point of interest (POI).

![](assets/places_ui_intro.png)


## Experience Platform Location Services workflow

Here is a high-level view of the Experience Platform Location Services workflow:

![](assets/places-workflow-diagram-lc-1.png)