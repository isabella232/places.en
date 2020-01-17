---
title: Test and validate Places Service
description: This section provides information about how you can test and validate Places Service.
---

# Recommendations to test Places Service {#test-validate-loc-svc}

Many customers and organizations will define POIs across the globe, so it is important to have a way to simulate and test how the Places Service interacts with your application.

This information helps you understand how to test and validate the Places Service entries and exits that are being correctly triggered based on the defined POIs and a user's current location.

Since environmental variables can be a factor in location signal and accuracy, we recommended that you first establish baseline results by working locally with developer tools and simulated location entries. The goal here is to validate that all location events are correctly working.

After the location events are correctly validated, solution integrations (for example, Analytics, Target, and Campaign) can be tested. To help your testing activities, you should set up Slack Webhooks with a postback and load GPX files in your individual development environment.

>[!IMPORTANT]
>
>This plan assumes that POIs have been created in the [Places Service management UI](https://places.adobe.com) and the latest versions of the the Places extension and Places Monitor extension are installed and correctly configured.

| Step | Description | Expected Result |
|--- |--- |--- |
| 1 | Confirm that the proper manifest keys have been entered for Android to grant access to track location. For more information, see [Add permissions to the manifest](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Confirmed |
| 1a | Confirm location updates are configured in iOS. Also ensure that you have the appropriate plist keys setup in iOS to request user permission to track location. For more information, see [Enable location updates in the background.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Confirmed |
| 2 | Confirm which monitoring mode is set for iOS. The continuous mode allows for greater accuracy and persistence but also more heavily drains battery life. For more information, see [Monitoring Mode (iOS only).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only)| Significant Changes or Continuous |
| 3 | If using more than one POIs library, confirm that the appropriate libraries have been selected in the Places extension for Experience Platform Launch. | Confirmed |
| 4 | Confirm that the latest versions of Mobile Core and Places/Places Monitor extensions have been bundled with the app via Gradle or CocoaPods.| Confirmed - for more information on recent updates see the [release notes.](/help/release-notes.md) |
| 5 | Confirm that the correct environments are configured for testing. The Launch environment ID should match your Launch development environment. |  Confirmed |
| 6 | Create GPX files for each POI that you want to test. GPX files can be used in local development environment to simulate a location entry. For information about creating and using GPX files, see the following: <br>[GPX files for iOS Simulator [closed]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[LOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX files are created and loaded in the app project. |
| 7 | Without doing anything else, you should be able to launch the application from Android Studio or XCode and see the appropriate alert to request access for the tracking location. Click the *Always Allow* permission.<br><br>We recommend that you use a real device that is connected to your computer instead of using device simulator. | Location request prompt should display on application loaded through IDE |
| 8 | Once Location permission has been accepted. The Places SDK will to retrieve the current location of the device and the Places Monitor extension will start monitoring the 20 closest POIs from the current location | See the log sample under the table. |
| 9 | Switching between different locations in XCode or Android studio should produce entry events for specific POIs. The below logs are expected on entry to a POI. | See the log sample under the table.|
| 10 | After you see the Places Monitor find nearby POIs, you should  test by sending location pings out. In Launch, create a new rule that uses the Places extension to trigger based on a geo-fence entry. Then create a new action by using Mobile Core to send a Postback. Creating a Slack Webhook app helps you see location entries and exits. For information on creating a Slack Webhook app see [Sending messages using Incoming Webhooks.](https://api.slack.com/messaging/webhooks)|  |
| 10a | In Launch, ensure that you added data elements for the Places extension including the following: <br>Current POI name<br>Current POI lat<br>Current POI long<br>Last Entered name<br>Last Entered lat<br>Last Entered long<br>Last Exited name<br>Last Exited lat<br>Last Exited long<br>Timestamp |  |
| 10b | Create a new rule with an Event = Places → Enter POI |  |
| 10c | Create an an action = Mobile Core → Postback |  |
| 10d | Use the Webhook URL for your Slack app, for example, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD….. |  |
| 10e | The post body would be similar to: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Ensure that you use the specific data elements that you created here. |  |
| 10f | Ensure that you publish all of the new data element and rule changes in Launch. (You should select a working dev library in the upper right of the Launch interface.)|  |
| 11 | Launch and test your application again by flipping between the GPX locations in the developer IDE. | You should now see Slack notifications showing entries for each POI as you select different locations in your development environment. |
|  | **QUICK SUMMARY POINT**<br>All of this testing can be conducted locally without having to go to a specific POI location. Validation testing helps ensure that your application is correctly configured and has received the correct permissions for the location. <br><br>This validation also gives you confidence that the defined POIs are working correctly with the Places Monitor extension.  After this step, we will begin to test messaging in Campaign to see if the proper messages appear based on POI entries and exits. |  |
|  | **Testing Adobe Campaign Standard In-App Messaging with Places Service.** |  |
| 12 | On the main Campaign dashboard configure a new In-App-Message (type = broadcast) |  |
| 12a | In triggers, select **Places event type - Entry as the trigger**. |  |
| 12b| Select **[UICONTROL Places Custom metadata]** as an additional filter - use POI type = Last Entered POI.<br>We use **[!UICONTROL Last Entered]** as the POI type because in most cases, **[!UICONTROL Last Entered]** will be the same as **[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]** should only be used in instances where there are overlapping POI geo-fences. In this case, these POIs need to be RANKED and then the **[!UICONTROL Current POI]** will display the top ranked POI out of the 2 or 3 geo-fences that a user might currently be in. |  |
| 12c | Select a custom metadata key that will help you narrow which POIs will receive a message. |  |
| 12d| For frequency and duration, keep to only one or two days, so that if you do not like the criteria, you can expire the trigger in a shorter period of time. |  |
| 12e | For Always/Once or Until click-through, select *ALWAYS* so that you can test across multiple locations. | An In-app message is displayed ALWAYS when you simulate a location change that meets the appropriate metadata criteria. |
| 12f | For the display, select an option other than Local Notification. This makes it easier to see when testing with the app in the foreground.) |  |
| 12g | Prepare/confirm and deploy the in-app message. |  |
| 13 | In your development environment, to ensure that new campaign rules are downloaded, quit and launch the application again.  | Do not forget that the applications must be completely launched again for the new Campaign rules file to be downloaded to the device. |
| 14 | In your development application, switch locations by using the previously created GPX files.  |  You should see the in-app message appear based on the previous criteria that was set.|
| 15 | For the next test, we will essentially copy the same steps as before, but this time we will test LOCAL NOTIFICATION. | The expected result is that the local notifications are displayed each time matching criteria is met. |
| 16 | Configure a new In-App-Message (type = broadcast). |  |
| 16a | In triggers, select **[!UICONTROL Places event type]** - **[!UICONTROL Entry as the trigger]**. |  |
| 16b | Select the Places Custom metadata as an additional filter - use **[!UICONTROL POI type]** = **[!UICONTROL Last Entered POI]**. |  |
| 16c | Select a custom metadata key that will help you narrow which POIs will receive a message. |  |
| 16d | For frequency and duration, keep only one or two days, so that if you do not like the criteria, you can expire the trigger in a shorter period of time. |  |
| 16e | For Always/Once or Until click-through, **[!UICONTROL ALWAYS]**. |  |
| 16f | For the display type, select **[!UICONTROL Local Notification]**. |  |
| 16g | Prepare/confirm and deploy the in-app message. |  |
| 17 | In the developer environment, connect your device and press **[!UICONTROL Play]** on the build. After you establish that location is working, background the application and continue switching locations in Xcode or Android Studio. You should still see console read-outs indicating the location change, and you should also see local notifications displayed depending on the criteria set in your trigger. (There might be a 1-2 second delay.)| The expected result is that local notifications are displayed each time the matching criteria is met. |
|  | **SUMMARY POINT** <br>At this stage, we should be seeing POI entries in our local environment. We should also see messaging from Campaign based on the POI work. If there are failures, check to see whether a Slack notification did not go out. If there is no Slack message, check the application console, because a new location entry might not have been recorded. If results are successful, then we can be fairly sure that the application is performing correctly and that the Places Service and Campaign messaging service is also working correctly.|  |
|  | **ON-SITE TESTING** <br>Not much should change when testing on location. Keeping the slack postback active should help with understanding if the device is getting an entry and exit for the location.|  |
| 18 | Conduct tests with devices starting out with wifi and cellular disabled and then enable once in the POI region. | If there is a failure, make note whether you are getting a geo-fence entry and notification in Slack. What is the timestamp on the Slack notification? |
| 19 | Conduct the test with only cellular enabled and with the wifi turned off. |  |
| 20 | Conduct test with both cellular and wifi turned on. |  |
|  | **SUMMARY POINT** <br>On-site testing should closely match the development testing. Keep in mind that there are some environmental factors that can come into play in determining a users location, such as duration of time spent in a POI geo-fence, availability of cell signal, and strength of nearby wifi access points.|  |

## Log Samples

**Step 8 :** Expected iOS and Android logs during a location update

  **iOS**

   ```
   [AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
   [AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
   [AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
   [AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
   <ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
   ..
   ..)   
   ```

  **Android**

   ```
   PlacesMonitor - All location settings are satisfied to monitor location
   PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
   PlacesExtension - Dispatching nearby places event with n POIs
   PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
   PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
   PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
   ...
   ...
   PlacesMonitor - Successfully added n fences for monitoring
   
   ```

**Step 9 :** Expected iOS and Android logs during an event

  **iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

  **Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
