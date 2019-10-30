---
title: Push notifications
seo-title: Push notifications
description: This section shows you how to use Places with push notifications.
seo-description: This section shows you how to use Places with push notifications.
---

# Push notifications (#places-push-messaging)

Mobile Services allows you to send push notifications to Adobe Analytics segments. In Location Service, you can segment the audience for your push message by using their historical interactions with your POIs. For example, you can send a message to users who have been in one of your stores in the last 30 days.

Before you begin, ensure that you have completed the following tasks:

* Location Service data has been processed by Adobe Analytics.

  This means that your mobile app has successfully sent Location Service data into a Report Suite and that the data is available for segmentation.

* The push notification channel in Mobile Services is set up.

  For more information, see [Create a push message](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Understand how to send a push notification to an Analytics segment in Mobile Services.

  For more information, see [Create a push message](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Send a notification

On the **[!UICONTROL Audience]** tab of the *Create push notification* workflow, you can create the audience for this message in one of the following ways:

* In the **[!UICONTROL Analytics Segments]** drop-down list, select a previously created Adobe Analytics segment.

* In the **[!UICONTROL Custom Segment]** section, build an audience by using the available custom segment parameters.

![setting up a push message](/help/assets/push-set-up.png)