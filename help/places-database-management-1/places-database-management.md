---
title: Overview
seo-title: Places database management
description: POIs are created and managed in the Places database. This can be done using APIs, or using our product interface. 
seo-description: POIs are created and managed in the Places database. This can be done using APIs, or using our product interface. 
---

# Places datatabase management 

POIs are created and managed in the Places database. This can be done using APIs, or using our product interface. 

## Size and reliability  

Important to note for all geofences being used in region monitoring from a mobile app regardless of using Adobe or some other service. The Operating systems recommend some parameters to keep in mind when creating geofences. For maximum reliability, geofences should have a radius of at least 100 meters. It is okay to create smaller geofences, but entry and exit events may not be generated, or may be generated after the user stops moving for a period. 

In addition, accuracy and reliability may be reduced based on hardware conditions such as wi-fi being turned off or unavailable, and also based on the device's location in relation to hampering gps signals. For example, mountainous areas, urban settings, and indoor areas can reduce location accuracy from the iOS and Android operating systems.  
