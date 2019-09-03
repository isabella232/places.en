---
title: Using Places with Adobe Campaign Standard
seo-title: Using Places with Adobe Campaign Standard
description: Having a deep understanding your customers preferences and habits are key to any successful marketing campaign. Knowing if a user has visited a physical location can also add some very valuable context in forming a relationship with the consumer.
seo-description: Having a deep understanding your customers preferences and habits are key to any successful marketing campaign. Knowing if a user has visited a physical location can also add some very valuable context in forming a relationship with the consumer.
---

# Using Places with Adobe Campaign Standard

*Thanks for visiting us last week, we’d love to give you a surprise for use on your next visit!*

Having a deep understanding your customers preferences and habits are key to any successful marketing campaign. The items a user has searched for and previous purchase history play a big role in audience targeting. Knowing if a user has visited a physical location can also add some very valuable context in forming a relationship with the consumer.

According to a recent report from eMarketer, 85% of high-performing retailers believe that location is very important to their marketing efforts. Additionally, over 58% of retailers in North America are planning to invest in proximity/location technologies to enhance their customer experiences.

![](/help/assets/using-loc-services-acs_0.png)

Think about how critical location is in your smartphone usage experience. How often do ask your smartphone to find nearby restaurants, gas stations, grocery stores or other services.

It makes sense then that as a brand you should be thinking of ways to leverage location into your marketing campaigns. In this guide we’ll show how you can harness the power of Adobe Experience Platform Location Service to add location context to messaging through Adobe Campaign Standard, allowing you to blast out personalized push notifications or in-app messages based on historical point of interest (POI) entry.

Before we begin, this guide assumes that you have a mobile application configured with the Adobe Experience Platform Mobile SDK with the Adobe Campaign Standard extension. In addition to Adobe Experience Platform Mobile SDK and Campaign Standard, you should have access to Location Service.

## Prerequisites

1. Integrate the [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) into your app.
2. Add the [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) to your mobile app configuration.
3. [Create one or more POIs](/help/loc-services-database-management-1/managing-pois-in-the-loc-services-ui.md#create-a-poi) in Adobe Experience Platform Location Services.

  >[!TIP]
  >
  >If you are looking for ways to bulk upload or manage POIs, take a look at this [script to upload POIs from a CSV](https://github.com/adobe/places-scripts) file. Additionally, the [Location Service APIs](/help/loc-services-rest-apis/api-usage/api-usage.md) can be used to create or manage points of interest.

If you do not have access to Location Services, you can [request access here](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u).

### Enable and install the Places extensions in your application

After creating points of interest in the Adobe Experience Platform Location Services interface, you will need to add the Places functionality to your application.

1. Follow the directions for enabling the Places and Places Monitor extensions in your application.

2. In the Places extension make sure you have selected the appropriate library of POIs that you created previously. 

    Additional libraries can be added to the extension configuration at any time.

3. Ensure that you have added these configurations to a Library and published the configuration changes in Launch.

4. In the Launch environments tab, click on the install instructions icon to view instructions on downloading the appropriate CocoaPod and Gradle files to your app project.

5. In your application, follow the instructions for adding Location background mode to your application, and start the Places Location Monitor.

6. Test your application through a device simulator to see the application request nearby points of interest based on spoofing the device’s location.

### Create Data Elements in Experience Platform Launch

After you verify that you have the Places and Places Monitor extensions working correctly in your application, create data elements in Launch to read the information that is provided by the extensions and is coming through the Mobile SDK event hub. Data elements essentially act as an alias to retrieve data from the client application. Let’s create a few data elements to retrieve data from the Places extensions.

1. In your Launch mobile property, on the **[!UICONTROL Data Elements]** tab and click **[!UICONTROL Add Data Element]**.
2. From the extension menu, select **[!UICONTROL Places]**.
3. From the **[!UICONTROL Data Element]** drop-down list, select **[!UICONTROL Name}**.
4. In the window to the right, you can select **[!UICONTROL Current POI]** which will retrieve the name of the POI that the user is currently in. 

    * **[!UICONTROL Last Entered]** retrieves the name of the POI that user last entered a
    * **[!UICONTROL Last Exited]** will provide the name of the POI that the user last left.

5. Select **[!UICONTROL Last Entered]**.

6. Type a name for the data element, such as **[!UICONTROL Last Entered POI Name]**, and click **[!UICONTROL Save]**. 


    ![](/help/assets/using-loc-services-acs_1.png)

7. Repeat the same steps above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, *Last Entered POI Radius*.

In addition to the data elements for Places, make sure you have also created Mobile Core data elements for *App ID* and *Experience Cloud ID*.

### Create a Rule to send Location Data to Adobe Campaign Standard

Rules in Experience Platform Launch allow you to create complex multi-solution workflows based on event triggers. You can create new ones or make changes to existing rules and have the updates dynamically deployed to your mobile applications. In this example, we will create a rule that is triggered when a user enters a geo-fenced POI. After the rule is triggered, an update is sent to Campaign Standard to record an entry to a specific POI for the user. This POI is based on Experience Cloud ID.

1. In your Experience Platform Launch mobile property, click the **[!UICONTROL Rules]** tab and click **[!UICONTROL Add Rule]**.
2. In the **[!UICONTROL Events]** section, click **[!UICONTROL +]** and select **[!UICONTROL Places]**.
3. In **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
4. Enter a name for the rule, for example, **[!UICONTROL User entered POI]**.
5. Click **[!UICONTROL Keep Changes]**.
6. Leave the **[!UICONTROL Conditions]** section blank.

    This section allows you to filter or place restrictions on when this rule should fire. 

7. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
8. In **[!UICONTROL Extension]**, select **[!UICONTROL Mobile Core]** and, in **[!UICONTROL Action Type]**, select **[!UICONTROL Send Postback]**. 

9. For the URL, you need to construct your Campaign Standard locations endpoint. 

    The URL should look similar to the one below. Make sure you use the correct data elements that you created previously for your Campaign server and pKey.

    `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

10. Click the box to add a post body and send the following:

    ```text
    {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
    }
    ```

11. Use the specific data elements that you created in the previous section.

12. In **[!UICONTROL Content Type]**, type **[!UICONTROL application/json]**.

13. Click **[!UICONTROL Keep Changes]** after you have this set up.

    It might be helpful to set up a Slack web hook as an additional action to validate that my action is being triggered and that the right data is being collected.

    >[!IMPORTANT]
    >
    >Remember to publish the recent changes to your app to make sure the rule and all of your data elements are deployed as part of your configuration. After publishing, you should re-launch the mobile application to get the latest configuration updates.

### Use Location Data to target Campaign Standard messages

Now that we have location data populated in Campaign, we can use points of interest as an audience segment tool.

1. Inside of your Adobe Campaign Standard instance click the “Create Push Notification” button

2. For the push notification type, select “Send push to app subscribers”. 

    This push type will target all users of your application. You can also select “Send push to Campaign profiles” if your mobile user’s are attached to a Campaign profile.

3. Click **[!UICONTROL Next]** and type the general details on the next screen.

4. On the Audience screen, click **[!UICONTROL Count]** to see to how many estimated user the push notification will be sent. 

    In this case, my count will equal three, as I have three devices that I have installed test application on.

5. On the left sidebar, expand the **[!UICONTROL Profile]** tab and drag the **[!UICONTROL POI location]** filter onto the main area.

6. In the POI filter window, enter the exact name of the POI that you wish to target. 

    You can make additional selections to determine the range of time since the user’s last visit to this POI.

    ![](/help/assets/using-loc-services-acs_2.png)

7. Click [!**UICONTROL Confirm]**.
8. Run the count again at the top to see your audience size change. 

    If you are not seeing your count update, it could be that you entered a POI name for which no devices have triggered an entry. This is where having the Slack web hook becomes valuable, as you can see a listing of POI entries from various test devices.
9. You can drag out additional POI location filters to include multiple POIs in your message.
10. Click **[!UICONTROL Next]** to finish creating the push notification for delivery.

    ![](/help/assets/using-loc-services-acs_3.png)

In addition to push notifications, you can also use location data to segment which users you would like to receive an in-app message.

1. In your Adobe Campaign Standard instance click **[!UICONTROL Create In-App message]**.
2. For the message type select **[!UICONTROL Target all users of a Mobile application]**.
3. Click **[!UICONTROL Next]** and fill in the general details on the next screen.
4. You’ll see on the left sidebar that you can now use a variety triggers related to Places.
5. I can choose to have the in-app message display if the user has entered a POI geo-fence
6. I can also use metadata that I defined in the Location Services UI to filter my audience. 

      In this example I want to trigger an in-app message shown only to users that last exited a POI that also had a Gym facility. Perhaps I want to send them a survey to see if they used/liked the gym.

7. Click **[!UICONTROL Next]** to finish creating the in-app message for delivery.

    ![](/help/assets/using-loc-services-acs_4.png)

Using Adobe Experience Platform Location Services in conjunction with Adobe Campaign Standard gives you a very powerful tool to segment and target your messaging to users based on historical location. This simple integration opens the door for building out more personalized and contextual use cases.

We’re constantly evolving Adobe Experience Platform Location Services and the solutions integrated to bring location context into mobile workflows. One product that will take advantage of Platform Location Services, is the upcoming Triggered Journey’s solution that will allow customers to create real-time workflows based on event triggers such as location.

## Recommended Links

For more information, see the following:

* [Adobe Experience Platform Location Service](https://www.adobe.com/experience-platform/location-service.html)

* [Adobe Campaign Standard](https://www.adobe.com/marketing/campaign.html)

* [Sign-up for access to Adobe Location Service Beta](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)

* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)

* [Adobe Campaign integration with Experience Platform SDK](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)

