---
title: Add location context to Analytics requests
seo-title: Add location context to Analytics requests
description: This section provides information about how to Add location context to Analytics requests.
seo-description: This section provides information about how to Add location context to Analytics requests.
---

# Add location context to Analytics requests {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>This document assumes that you have Adobe Places implemented in your application. For more information about implementing Adobe Places, see [Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

After Places sends the entry and exit events, you can create rules in Experience Platform Launch and attach your Places data to all Adobe Analytics events. To create this type of rule, select your property in Launch and complete the following steps:

## 1. Create a rule

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

    Remember the following information:
    * If you do not have existing rules for this property, the **[!UICONTROL Create New Rule]** button will be in the middle of the screen.
    * If your property has rules, the **[!UICONTROL Create New Rule]** button will be in the top right of the screen.

## 2.Select an event

1. Give your rule a meaningful name so it will be easily recognizable in your list of Rules.

    In this example, the Rule is named **[!UICONTROL Attach Places Data to Analytics Track Action Events]**.

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Mobile Core]**.

1. From the **[!UICONTROL Event Type]** drop-down list, select **[!UICONTROL Track Action]**.

Now you can determine the triggers that you want to include for this Rule. In this example, the trigger is based on all `TrackAction` calls. After you configure the Event, click **[!UICONTROL Keep Changes]**.

!["create an event"](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Add conditions

>[!IMPORTANT]
>
>Complete this procedure to add Conditions to your rule. Otherwise, skip to the *Define the Action* section below.

In this example, a Condition is created that causes the Rule to trigger only for AT&T customers.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTORL Mobile Core]**.

1. From the **[!UICONTROL Condition Type]** drop-down list, select **[!UICONTROL Carrier Name]**.

1. In the window on the right, select the **[!UICONTROL AT&T]** checkbox.

1. Click **[!UICONTROL Keep Changes]**.

!["create a condition"](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Define the action

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Mobile Core]**.  

1. From the **[!UICONTROL Action Type]** drop-down list, select **[!UICONTROL Attach Data]**.

1. On the right pane, in the **[!UICONTROL JSON Payload]** field, type the data that will be added to this Event.

1. Click **[!UICONTROL Keep Changes]**.

On the right pane, you can add a freeform JSON payload that adds data to an SDK event before an extension that is listening for this event can hear the event. In this example, some context data is added to this event before the Analytics extension processes it. The added context data will now be on the outgoing Analytics hit.

In the following example, `poi.city` and `poi.name` values are added to the context data of the Analytics event. The values for the new keys are dynamically determined by the SDK when this event processes.

!["create an action"](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Save the rule and rebuild your property

After you complete your configuration, verify that your Rule looks like the following image:

!["the rule is complete."](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Click **[!UICONTROL Save]**

1. Rebuild your Launch property and deploy it to the correct Environment.
