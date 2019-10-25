---
title: Run reports in Adobe Analytics that includes Places data
seo-title: Run reports in Adobe Analytics that includes Places data
description: This section provides information about how to run reports in Analytics that includes Places data.
seo-description: This section provides information about how to run reports in Analytics that includes Places data.
---

# Run reports in Adobe Analytics that includes Places data {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>This document assumes that you have Adobe Places implemented in your application. For more information about implementing Adobe Places, see [Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

After Places sends the entry and exit events, you can create rules in Experience Platform Launch and attach your Places data to all Adobe Analytics events. To create this type of rule, select your property in Launch and complete the following steps:

## 1. Create a Rule

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

    Remember the following information:
    * If you do not have existing rules for this property, the button will be in the middle of the screen.
    * If your property has rules, the button will be in the top right of the screen.

## 1.Select an Event

1. Give your rule a meaningful name so it will be easily recognizable in your list of Rules. 

    In this example, the Rule is named **Attach Places Data to Analytics Track Action Events**.

2. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Mobile Core]**.

4. From the **[!UICONTROL Event Type]** drop-down list, select **[!UICONTROL Track Action]**.

Now you can determine the triggers that you want to include for this Rule. In this example, the trigger is based on all `TrackAction` calls. After you configure the Event, click **[!UICONTROL Keep Changes]**.

!["create an event"](assets/ad-setEvent.png )


## 2. Add Conditions

>[!IMPORTANT]
>
>Complete this step if you want to add Conditions to your rule. Otherwise, skip to the *Define the Action* section below.

In this example, a Condition is created that causes the Rule to trigger only for AT&T customers.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

2. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTORL Mobile Core]**.

3. From the **[!UICONTROL Condition Type]** drop-down list, select **[!UICONTROL Carrier Name]**.

4. In the window on the right, select the **[!UICONTROL AT&T]** checkbox.

5. Click **[!UICONTROL Keep Changes]**.

!["create a condition"](assets/ad-setCondition.png )

## 3. Define the Action

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

2. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Mobile Core]**.  

3. From the **[!UICONTROL Action Type]** drop-down list, select **[!UICONTROL Attach Data]**.

4. On the right pane, in the **[!UICONTROL JSON Payload]** field, type the data that will be added to this Event.

5. Click **[!UICONTROL Keep Changes]**.

On the right pane, you can add a freeform JSON payload that adds data to an SDK event before an extension that is listening for this event can hear the event. In this example, some context data is added to this event before the Analytics extension processes it. The added context data will now be on the outgoing Analytics hit.

In the following example, `poi.city` and `poi.name` values are added to the context data of the Analytics event. The values for the new keys are dynamically determined by the SDK when this event processes.

!["create an action"](assets/pt-setAction.png )

## 4. Save the Rule and rebuild your property

After you complete your configuration, verify that your Rule looks like the following image:

!["the rule is complete."](assets/pt-ruleComplete.png )

1. Click **[!UICONTROL Save]**

2. Rebuild your Launch property and deploy it to the correct Environment.
