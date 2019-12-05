---
title: Send POI entry and exit data to Analytics
description: This section provides information about how to send POI entry and exit data to Analytics.
---

# Send POI entry and exit data to Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>This section assumes that you have Places implemented in your application. For more information about implementing Places, see [Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md).

After Places sends the entry and exit events, you can create rules in Experience Platform Launch to send Places data to Adobe Analytics. To create this type of rule, select your property in Launch and complete the following steps:

## 1. Create a rule

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

    Remember the following information:

    * If you do not have existing rules for this property, the **[!UICONTROL Create New Rule]** button will be in the middle of the screen.
    * If your property has rules, the **[!UICONTROL Create New Rule]** button will be in the top right of the screen.

## 2. Select an event

1. Type a meaningful name for your rule.

    This way, the rule will be easily recognizable in your list of Rules. In this example, the Rule is named **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Places]**.

1. From the **[!UICONTROL Event Type]** drop-down list, select **[!UICONTROL Enter POI]**.

1. Click **[!UICONTROL Keep Changes]**.

   !["select an event"](/help/assets/pt-selectEvent.png)


## 3. Add conditions

>[!IMPORTANT]
>
>Complete this step to add Conditions to your rule. Otherwise, skip to *Define the Action* below.

In this example, a Condition is created that causes the Rule to trigger only when the Current POI's name equals **[!UICONTROL My POI]**.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Places]**.

1. From the **[!UICONTROL Condition Type]** drop-down list, select **[!UICONTROL Name]**.

1. In the right pane, in the text field, enter **[!UICONTROL My POI]**.

1. Click **[!UICONTROL Keep Changes]**.

   !["set a condition"](/help/assets/pt-setCondition.png)


## 4. Define the action

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. From the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Adobe Analytics]**.  

1. From the **[!UICONTROL Action Type]** drop-down list, select **[!UICONTROL Track]**.

1. On the right pane, add the action or state that you want to send to Analytics.

    You can also choose to add any additional context data to this request. Remember that you can use data elements to get this data dynamically from the SDK.

1. Click **[!UICONTROL Keep Changes]**.

    In the following example, a `TrackAction` call is sent to Analytics with additional context data of `poi.name` equal to the name of the POI that triggered this entry event:

    !["set an action"](/help/assets/pt-setAction.png)

## 5. Save the rule and rebuild your property

After you complete your configuration, verify that your Rule looks like the following image:

!["rule is created"](/help/assets/pt-ruleComplete.png)

1. Click **[!UICONTROL Save]**

1. Rebuild your Launch property and deploy it to the correct environment.
