---
title: Using metadata with POIs
seo-title: Using metadata with POIs
description: This section provides information and strategies about how to use metadata with POIs.
seo-description: This section provides information and strategies about how to use metadata with POIs. 
---

# Strategies for using metadata with POIs {#using-metadata-pois}

In Location Service, when you create a a new POI, the only required elements are Name, Radius, Latitude and Longitude. For more information about creating a POI, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md). If, however, you are only entering the minimum information, you will miss an opportunity to create additional value.

Point of interest metadata can be used in a variety of ways. From a POI management standpoint, adding metadata values can aid in searching for or filtering a list of potentially thousands of POIs. Creating metadata for key attributes related to a POI can yield value in downstream workflows. For instance, a hotel chain creating POIs for each property may want to include metadata such as if the hotel property has a pool or not, or a restaurant and bar, or if they have a gym facility. This metadata can be included as context data in analytics and can also be used for targeted offers or messaging.

## Location Service metadata in Launch

In Adobe Experience Platform Launch you can create data elements for each Location Service metadata field that is important for tracking or messaging purposes.

![data element for the gym facility](/help/assets/gymfacility.png)

You can then create an action with the Analytics extension for creating a new hit that includes whatever metadata you would like as context data.

![action for the gym facility](/help/assets/Analytics-gym.png)

## In-App Messaging in Adobe Campaign

Metadata can be used as a filter for local notifications and in-app messages defined in Adobe Campaign Standard. Using metadata as a filter affords the opportunity to create a more relevant message that is contextual to the actual location.

![filtering local notifications and in-app messages in ACS](/help/assets/ACS_gym_metadata.png)