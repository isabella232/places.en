---
title: Using Places with Mobile Services for messaging
description: This section shows you how to use Places with Mobile Services for messaging.
---

# Adobe Mobile Services {#places-mobile-services}

Before you can use Mobile Services extension for messaging, review the following prerequisites:

* Points of interest have been created in the Location Service. See Documentation if needed. (link to creating a POI)
Note: The Location Service includes a new and improved point of interest database for your organization that exists outside of the legacy AMS interface. Any POIs found in AMS’s ‘Manage Places’ navigation will only work for version 4 of the SDK. 
  * Here is the legacy Places POI management interface within AMS for older versions of SDK:

    ![Legacy UI](/help/assets/legacy-location-v4-ui.png)

  * Here is the Location Service POI management interface:

    ![Location Service POI management UI](/help/assets/places-ui.png)

* ACP SDK is properly configured with Places and/or Places Monitor extensions. This means that data is available as events and/or conditions in the Launch rules engine for your mobile app. See documentation if needed. (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* Familiar with how to create and publish Launch rules to the ACP SDK in your mobile app. See documentation if needed. (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* Launch Data Elements are created from Places SDK extension data that will be used in the Rules. See documentation (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements) 

## Reporting 

Before you can use reporting, complete the following prerequisites:

* Successfully sending Location Service data into Adobe Analytics Report Suite. Please visit Adobe Analytics documentation if needed (link to Steve’s docs).
* Familiar with AMS reporting. Please visit documentation if needed (https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)

## Reporting visualization 

You can run AMS reports using Location Service data that is sent to Adobe Analytics. For example, I have sent in events when users have entries in one of my POIs. In this report I have added a filter of the POI entry event on top of my out-of-the-box user report:

![Report visualization](/help/assets/report-visualize.png)

Additional flexibility in visualizing Location Service data is available within the Adobe Analytics interfaces.  

