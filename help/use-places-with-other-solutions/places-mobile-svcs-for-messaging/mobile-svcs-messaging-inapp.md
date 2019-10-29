---
title: In-App notifications
seo-title: In-App notifications
description: This section shows you how to use Places with In-App messaging.
seo-description: This section shows you how to use Places with In-App messaging.
---

# In-App notifications (#places-push-messaging)

The following information shows you how to configure In-App messages to trigger from Places events.

>[!IMPORTANT]
>
>The messages must be on an Analytics hit.

## In-app message

Mobile Services allows you to use location data that is being sent to Analytics as the trigger event(s) and/or condition for an in-app message. If In-App messages are fired from the SDK and do not need to wait for data to be processed by Analytics, the messages can appear in real time as soon as the trigger occurs.

### Local notifications

Here is a list of the available In-app messaging types:

* Full screen
* Alert
* Local notifications

These types are in-app messages because they are triggered by the SDK. Local notifications look and feel like push notifications because they appear when the app is in the background. These notifications also deliver real-time notifications as users enter or exit your POIs while the app is in the background. For more information see [Places Monitor extension.](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)

### Prerequisites

Before you begin, you understand how to send and create an in-app message in Mobile Services and how triggers work. For more information, see [Create an in-app message.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Rules in Experience Platform Launch

You can create Launch rules that send the data that you want to be able to use as part of your in-app message Trigger rules to Analytics. You can use data from the Places extensions in your Launch rules as either events and/or conditions depending on your use case.

* Using location data as the triggering event.

  For example, you can send data to Analytics when a user enters a POI.

* Using location data as a Condition to a triggering event.

  For example, if you created a custom metadata tag in the Location Service for the weather at different POIs, you can use that metadata as a parameter for your Rule condition. While you can use this condition with a POI entry event described earlier, you can also use the condition as context to any event.

After the rule is set up with the proper event and condition parameters, complete your rule configuration by configuring the action to send data to Analytics. 

## Create an action

To do this:

1. Select the **[!UICONTROL Adobe Analytics]** extension.
1. In the **[!UICONTROL Action type]** drop-down list, select **[!UICONTROL Track.]**
1. Type a name for your action.
1. In the right pane, in **[!UICONTROL Context Data]**, select the key and value pair to set the context data that will be sent to Analytics. 

  For example, you can select **[!UICONTROL poiname]** as the key and **[!UICONTROL `{%%Last Entered POI Name}`.]

>[!TIP]
>
>Analytics Processing Rules can be set to pick up this context data. For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). In the example in *Create an action*, the Action will send the `poiname` as the context to describe the POIentry event that is being sent to Analytics.

![creating an action](/help/assets/configure-action.png)

Here is an example of the complete rule: 

![completed rule](/help/assets/create-a-rule.png)

## Creating an in-app message in AMS

As part of your Trigger parameters, you can create the audience for the message with data from the Location Service in one of the following ways:

* Using location specific actions such as an entry or an exit.
* Using POI metadata that is sent as context data to narrow the target of your audience.

  This optin can be used with a location-specific action, such as entry, or it can be used as context to another event such as a launch or a button click. 

  Here is an example of how to configure an in-app message to welcome users who enter a POI that has **[!UICONTROL Adobe]** in the name:

  ![trigger parameters](/help/assets/trigger-parameters.png)

* Parameters in the Places headings in the *Triggers and Traits* page in Mobile Services do not work with data from the Location Service. Those parameters are only for the legacy Places database that was created in Mobile Services.  