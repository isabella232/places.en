---
title: In-App messages with Location Service
seo-title: In-App messages with Location Service
description: This section provides information about how to use Push messaging in Campaign Standard with In-App messages in Campaign Standard.
seo-description: This section provides information about how to use "Push messaging in Campaign Standard" with In-App messages in Campaign Standard. 
---

# In-App messaging with Location Service {#in-app-messages-loc-service}

(video from Ivan.)

This information helps you understand how you can use Adobe Experience Platform Location Service information to send In-App Messages or Local Notifications.

>[!IMPORTANT]
>
>Before you begin, complete the following tasks:
>
>* Have a mobile application configured with the Adobe Experience Platform Mobile SDK, including the [Adobe Campaign Standard extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard). 
>
>* Integrate the [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) into your app.
>* Add the [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) to your mobile app configuration.
>
>* [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in the Places POI management interface.
>
>* Install and configure the [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md) and [Places Monitor extensions](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) in your mobile application.

## Sending an In-App message based on a geo-fence entry or exit

1. In your Adobe Campaign Standard instance, click **[!UICONTROL Create In-App message]**.
2. For the message type select **[!UICONTROL Target all users of a Mobile application]**.
3. Click **[!UICONTROL Next]** and type the general details.
4. In the left pane, verify that you can now use a variety triggers related to Location Services.

    * You can choose to have the in-app message display if the user has entered a POI geo-fence.
    * You can also use metadata that defined in the Location Services UI to filter audience.
 
    In the example in the following graphic, you can trigger an in-app message that is displayed only to users who entered one of the vacation resorts that are participating in a free drink program, you want to send your users a coupon when they arrive.

   ![In-App Message Places metadata](assets/last-entered-vacation.png)

5. Click the **[!UICONTROL Next]** to finish creating the In-app message for delivery.

    ![create an event](assets/prepare-ACS.png)

    To test the in-app message delivery, launch the application in Xcode or Android studio and use the location simulator to select a POI hat fits the messaging criteria.

    ![drink coupon](assets/drink-coupon-on-app.png)


Using Location Services with Adobe Campaign Standard gives you a powerful tool to segment and target your messaging to users based on geo-fence entries and exits. This simple integration opens the door to build more personalized and contextual use cases.

## Create different triggers in Campaign Standard based on Places metadata

(is this information coming?)