---
title: Using Places Service with Mobile Services for messaging
description: This section shows you how to use Places Service with Mobile Services for messaging.
---

# Adobe Mobile Services {#places-mobile-services}

Before you can use Mobile Services extension for messaging, review the following prerequisites:

* Points of interest have been created in Places Service. For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

    >[!IMPORTANT]
    >
    >The Places Service includes a new and improved POI database for your organization that exists outside the legacy Mobile Services UI. POIs that are located on the Mobile Service *Manage Placess* page navigation will only work for version 4 of the SDK. 

* Here is the *Manage Places* POI management page in the legacy Mobile Services UI for older versions of the SDK:

    ![Legacy UI](/help/assets/legacy-location-v4-ui.png)

* Here is the Places Service POI management interface:

    ![Location Service POI management UI](/help/assets/places-ui.png)

* The ACP SDK is properly configured with Places and/or Places Monitor extensions. 

  This means that data is available as events and/or conditions in the Experience Platform Launch rules engine for your mobile app. For more information, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md) or [Places Monitor extension](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md).

* Become familiar with creating and publishing Experience Platform Launch rules to the ACP SDK in your mobile app. 

  For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch data elements are created from Places extension data that will be used in the Rules engine.

  For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Reporting 

Before you can use reporting, complete the following prerequisites:

* Successfully send Places Service data into Adobe Analytics Report Suite. 

    For more information, see [Use Places Service with Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md). 

* Become familiar with Mobile Services reporting. 

  For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Reporting visualization 

You can run Mobile Service reports using Places Service data that is sent to Adobe Analytics. In the following example, events are sent when users have entries in one of the POIs. In this report a filter of the POI entry event has been added over the out-of-the-box user report:

![Report visualization](/help/assets/report-visualize.png)

Additional flexibility in visualizing Places Service data is available in the Adobe Analytics interfaces.  

