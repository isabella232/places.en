# Overview

Location is the most personal context for designing and delivering personalized experiences. Places enables mobile apps with user location awareness in relation to Points of Interest \(POIs\).

The goal of Places is to help you achieve the following:

* Manage a database of POIs with rich metadata that can be leveraged across the Experience Cloud.
* Easily monitor device location from the context of your POI database.
* Take action from location signals in real time, when it matters, to provide personalized experiences that delight your users.

For example, Places could be used to: 

* Send a real time notification when someone enters a store.
* Analyze foot traffic of owned stores versus competitor stores.
* Segment an audience based on offline behavior.
* Target user with an in-store experience when relevant.

## Places Components

Places comprises the following components:

* Places database: Create and manage POIs using the Places management UI or Places REST APIs For more information, see[ Places database management](https://launch.gitbook.io/places-services-by-adobe-documentation/places-database-management-1).
* Places SDK: manages device location in relation to POIs from the Places database. For more information, see [Places SDK extensions \(Beta\)](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/places-extension).
* Places rules: Adobe Launch rules are enabled with entry and exit events and conditions from the Places database. 



## Terminology

Here are some common terms that are used in the Places documentation:

* A **point of interest \(POI\)** is a location that is of interest to your organization. Places creates a databased of POIs that you define. You can define POIs with attributes such as a name, radius, address, category and metadata tags.
* A **geofence** is a type of POI. This type is a virtual geographic boundary defined by latitude and longitude coordinates.
* A **beacon** is a type of POI. This type is a physical device that represents a location by emitting a low power bluetooth signal. Beacons are not currently supported in Places.
* A **library** is a collection of POIs.  
* A SDK **extension**, in Adobe Launch extensions are are used in conjunction with the AEP SDK to provide additional functionality while using shared data from the SDK.
* An **organization** is the entity that enables an administrator to configure groups and users, and to control single sign-on in the Experience Cloud.  The organization functions like a log-in company that spans all the Experience Cloud products and solutions. Most often, an organization is your company name. However, a company can have more than one organization.
* The **orgID** is the ID that represents your organization across AEP.  For more information, see [Finding your orgID](https://forums.adobe.com/thread/2339895).
* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.  For more information, see [Overview](https://marketing.adobe.com/resources/help/en_US/mcvid/).

## Places workflow

Here is a high-level view of the Places workflow:

![](.gitbook/assets/places-workflow-diagram-lc-1.png)

