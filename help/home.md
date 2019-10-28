---
title: Adobe Experience Platform Location Service
seo-title: Adobe Experience Platform Location Service
description: Location Service is an important context for understanding the engagement of mobile users. By using this context, mobile app developers can enhance the app design and make it a more personalized and engaging experience. 
seo-description: Location Service is an important context for understanding the engagement of mobile users. By using this context, mobile app developers can enhance the app design and make it a more personalized and engaging experience. 
---

# Overview {#home}

Adobe Experience Platform Location Service (Location Service) is an important context for understanding the engagement of mobile users. By using this context, mobile app developers can enhance the app design and make it a more personalized and engaging experience. Places is a geo-location service that enables mobile app developers to understand the location context by using rich and easy-to-use SDK interfaces accompanied by a flexible database of points of interests (POIs).

Location Service allows you to achieve the following:

* Create and manage a database of POIs that can be leveraged with other Adobe Experience Cloud solutions.
* Attach custom metadata to the POIs to make them richer and more meaningful by specifying additional attributes. 
* Visualize the POIs on a map to easily understand the spatial context and add/edit metadata attributes. 
* Configure the SDK in Adobe Experience Platform Launch to define your location-triggered rules and metadata based conditions.
* Reduce the code that you need to write to a monitor device's location and use Adobe's location monitor to automatically trigger the location-specific rules.

This will allow you to take actions from location signals in real time, when and where it matters. The right context provides a more enriching mobile engagement experience.

Here are some of the ways you can use Places: 

* Send a real time notification when someone enters a POI, *"Hey..welcome to the stadium."* 
* Analyze foot traffic of your own stores versus your competitor stores.
* Segment an audience based on offline behavior by using audience profiles with location context.
* Target a user with an in-store experience when relevant.

## Location Service Use Cases

Improve this section with 

## Location Service components

Location Service comprises the following components:

* **Places web service** 

  You can create and manage POIs by using the Places REST APIs. For more information about the REST APIs, see [Manage libraries](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) and [Manage POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Location Service UI** 

  Visualize POIs on a map to understand the spatial context and to add/edit POIs and their custom metadata.

* **Places SDK** 

  The multi-platform mobile API interface to integrate the location context in your mobile apps. For more information about the SDKs, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Places rules** 

  The geo-intelligent Launch rules that enable you to trigger actions with entry and exit events. The rules also allow you to use geo-attributes in conditions to personalize the experience. 

* **Places Monitor**  
  
  The multi-platform mobile SDK which can be embedded in your mobile app to automatically monitor your user's location changes and trigger Places rules. For more information, see [Places Monitor extension](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## Terminology

Here are some common terms that are used in this documentation:

* A **point of interest (POI)** is a geo-location that is of interest to your organization.  

  You can define POIs with attributes such as a name, radius, address, category, and metadata tags.

* A **geofence** is a type of POI.  

  This POI type is a virtual geographic boundary that is defined by latitude and longitude coordinates.

* A **beacon** is a type of POI.  

  This POI type is a physical device that represents a location by emitting a low power bluetooth signal. Beacons support is coming in a future release.

* A **library** is a collection of POIs, which are grouped to easily attach rules to a set instead of one POI. 

* A SDK **extension**, is the Experience Platform Launch extension that is required to integrate the Places SDK in your mobile apps. 

  The extension used with the other mobile SDKs to add location context to your experiences.

* An **organization** is the Adobe entity that identifies your company in the Adobe Experience Cloud. 

  Typically, an organization is your company name. However, a company can have more than one organization. The organization administrator can configure groups and users and configure single sign-on functionality.

* The **orgID** is the ID that represents your organization across Adobe Experience Platform.

  For more information, see [Finding your orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. 

  For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).