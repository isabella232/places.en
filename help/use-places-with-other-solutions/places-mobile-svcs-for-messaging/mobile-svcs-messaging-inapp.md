---
title: In-App messaging
seo-title: In-App messaging
description: This section shows you how to use Places with In-App messaging.
seo-description: This section shows you how to use Places with In-App messaging.
---

# In-App notifications (#places-push-messaging)

How to configure In-App messages to trigger from Places events; the messages must be on an Analytics hit. 

## In-app message

AMS allows you to use location data that is being sent to Analytics as the trigger event(s) and/or condition for an in-app message. In-app messages can appear to the user in real time as soon as the trigger if fired from the SDK and does not need to wait for data to be processed by Analytics. 
•	Local notifications: In-app messaging has 3 different types: Full screen, ¬¬¬Alert, or Local Notifications. These types qualify as in-app messages because they are triggered by the SDK, but it is important to note that local notifications look and feel like push notifications as they appear while the app is not in the foreground. Local notifications are a great option for delivering real time notifications to users as they enter or exit your POIs while the app is in the background. Please see Places Monitor extension documentation to understand location monitoring (https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension¬¬¬¬¬)

### Pre-requisites

* Understand how to send and create an in-app message in AMS and how Triggers work. 

  For more information, see [Create an in-app message](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html).


## Create a rule in Experience Platform Launch

Create Launch rule(s) that sends the correct data to Analytics that you want to be able to use as part of your in-app message Trigger rule(s). You can use data from the Places extensions in your Launch rules as either events and/or conditions depending on your use case. 

* Using location data as the triggering event. For example, if you want to send data to Analytics when a user enters a POI.

* Using location data as a Condition to a triggering event. For example, if you created a custom metadata tag in the Location Service for the weather at different POIs, you can then use that metadata as a parameter for your Rule condition as shown below. Although you could use this condition to with the POI entry event described earlier, you could also use it as context to any event. 

Once the rule is set up with the proper event and condition parameters, finish your rule configuration by configuring the action to send data to Analytics. To do this:

* Select Adobe Analytics as the extension
* Choose “Track” as the action type
* Determine a name for your action
* Set Context Data to be sent in with the event. Use the Context Data interface to map Launch Data Elements to the key names you want sent to Analytics. 

Note that Analytics Processing Rules can be set to pick up this context data. See Analytics Processing Rules if needed (https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)
For example, this Action is sending in the poiname as context to describe the POIentry event that is being sent to Analytics.

![creating an action](/help/assets/configure-action.png)

Here is an example of what the finished rule could look like. 

![completed rule](/help/assets/create-a-rule.png)

## Creating an in-app message in AMS:

You will create the audience for the message with data from the Location Service as part of your Trigger parameters. 

* Using location specific actions such as entry or exit
* Using POI metadata that is sent in as context data to narrow the target of your audience. This can be used with a location specific action such as entry, or it can be used as context to another event such as a Launch or button click. 

  Here is an example of how you can set up an in-app message to welcome users that enter a POI that has “Adobe” in the name:

  ![trigger parameters](/help/assets/trigger-parameters.png)

* Parameters found in the ‘Places’ headings in AMS Triggers and Traits do not work with data from the Location Service. Those parameters are for the legacy Places database created in AMS.  