---
title: Frequently asked questions
description: This topic provides additional information about some frequently asked questions.
---

# Frequently asked questions

Here is some information and frequently asked questions about Location Service. 

## Size and reliability  

Important to note for all geofences being used in region monitoring from a mobile app regardless of using Adobe or some other service. The Operating systems recommend some parameters to keep in mind when creating geofences. For maximum reliability, geofences should have a radius of at least 100 meters. It is okay to create smaller geofences, but entry and exit events may not be generated, or may be generated after the user stops moving for a period. 

In addition, accuracy and reliability may be reduced based on hardware conditions such as wi-fi being turned off or unavailable, and also based on the device's location in relation to hampering GPS signals. For example, mountainous areas, urban settings, and indoor areas can reduce location accuracy from the iOS and Android operating systems. 

## How does an exit event trigger?

When the Places Monitor (SDK) gets a new list of nearby POIs, it registers a region with the operating system for each POI. The operating system is now responsible for notifying the SDK when the device crosses a boundary (entry or exit) for one of the monitored regions. The SDK only triggers an exit event when the operating system notifies the SDK that the event has occurred. The main reason for this notification is the time sensitivity of the location data.  

If the operating system cannot deliver an exit event when the device leaves a region, it is safer for the SDK to just omit the exit event. If the SDK manufactures an exit event without the event being triggered by the operating system, there is a risk that the exit event might be processed well outside the time period during which the device was near the POI.
