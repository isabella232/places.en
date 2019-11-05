---
title: Adobe Target
seo-title: Adobe Target
description: This section provides information about how to use Location Service with Adobe Target.
seo-description: This section provides information about how tto use Location Service with Adobe Target.
---

# Adobe Target {#places-target}

This document assumes that you have the Places extension implemented in your application. If you need help implementing Places extension, see [Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

After the Places extension is sending in events for entries and exits, you can leverage Rules in Launch to attach your Places data to your Adobe Target SDK events. With your desired property selected in Launch, you can create this type of rule by completing the following tasks:

## 1. Create a Rule

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

    Remember the following information:

    * If you do not have existing rules for this property, the button will be in the middle of the screen.
    * If your property has rules, the button will be in the top right of the screen.

## 2. Select an Event

1. Give your rule a meaningful name so it will be easily recognizable in your list of Rules.

    In this example, the Rule is named **[!UICONTROL Attach Places Data to Target Content Requested]**.

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Adobe Target]**.

1. From the **[!UICONTROL Event Type]** drop-down list, select **[!UICONTROL Content Requested]**.

1. Click **[!UICONTROL Keep Changes]**.

![add an event](/help/assets/ad-setEvent_target.png)

## 3. Add Conditions

>[!IMPORTANT]
>
>Complete this step if you want to add Conditions to your rule. Otherwise, skip to the *Define the Action* below.

In the following example, a Condition is created that causes the Rule to trigger only for users who have launched the app five or more times.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Mobile Core]**.

1. From the **[!UICONTROL Condition Type]** drop-down list, select **[!UICONTROL Launches]**.

1. On the right pane, modify the drop-down list and number controls so that the condition reads **[!UICONTROL User has launched the app greater than or equal to 5 times]**.

1. Click **[!UICONTROL Keep Changes]**.

![add a condition](/help/assets/ad-setCondition_target.png)

## 4. Define the Action

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Mobile Core]**.  

1. From the **[!UICONTROL Action Type]** drop-down list, select **[!UICONTROL Attach Data]**.

1. On the right pane, in the **[!UICONTROL JSON Payload]** field, type the data that will be added to this Event.

1. Click **[!UICONTROL Keep Changes]**.

On the right pane, you can add a freeform JSON payload that adds data to an SDK event before the extensions listening for this event hear it.

In the following example, `poiCity` and `poiName` values are added to the **[!UICONTROL mboxparameters]** for each request that is processed in the Target event. The values for the new keys are determined dynamically by the SDK at the time this event processes.

>[!TIP]
>
>This JSON payload uses a special notation for the `request` object. In the original event, `request` is an array of anonymous objects. When attaching data to all of objects in an array using Attach Data, the `[*]` notation on a key that is known to contain an array causes the payload to be applied to all objects in that array.
>
>The notation of `request[*]` can be read out loud as _for each object in the `request` array_.

![define the action](/help/assets/ad-setAction_target.png)

## 5. Save the Rule and rebuild your Property

After you complete your configuration, verify that your Rule looks like the following image:

![completed rule](/help/assets/ad-ruleComplete_target.png)

1. Click **[!UICONTROL Save]**

1. Rebuild your Launch property and deploy it to the correct Environment.
