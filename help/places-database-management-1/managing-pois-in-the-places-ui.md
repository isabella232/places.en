---
title: Manage POIs in the Places UI
seo-title: Manage POIs in the Places UI
description: Use the Places UI to manage your POIs.
seo-description: Use the Places UI to manage your POIs.
---

# Manage POIs in the Places UI

POIs and libraries are created and managed in the Places database by using the Places UI.

## Defining a geofence POI

Geofences are a type of POI and are defined in the database based by the following keys:

| Keys | Description | Required? |
| :--- | :--- | :--- |
| ID | Unique identifier assigned to each POI | Yes |
| Name | Friendly Name given to the POI | Yes |
| Library | Each POI must be assigned a library for organization | Yes |
| Icon | Assist with visualizations of the POIs | Yes (assigned default) |
| Color | Assist with visualizations of the POIs | Yes (assigned default) |
| Category | Assign a common framework of categories that are common across all POIs in all libraries | No |
| Address | Street address | No |
| City | city of POI | No |
| State/Region | state or region of POI | No |
| Country | country of POI | No |
| Latitude | Latitude coordinate for center of POI | Yes |
| Longitude | Longitude coordinate for center of POI | Yes |
| Metadata | custom key + value pairs that can be assigned to POIs. This metadata streamlines future workflows by allowing you to group POIs across libraries for each to use rules and filters in downstream workflows such as send a push notification whenever someone enter a POI with Type = Competitor. | No |

## Create a POI {#create-a-poi}

A point of interest (POI) is a location or a point on a map that is of interest to you. It can include locations like cafes, restaurants, and so on. 

1. Log in to Adobe Places with your Adobe ID.
2. In the top right side, click the icon that looks like a bulleted list and then click **[!UICONTROL New]**. 
3. Type a name for your POI.
4. Select or add a library.
5. Enter or select a radius.

    a. Select an icon for your POI.
    b. b. Select a color for the icon.

6. Expand the **[!UICONTROL Location]** section.

    a. Type an address.

    b. Type the city.

    c. Type the name of the state.

    d. Type the name of the country.

    e. Select or enter a latitude or longitude.

    f. Click **[!UICONTROL Drop Pin on Map]**.

7. Expand the **[!UICONTROL Metadata]** section and click **[!UICONTROL Add Metadata]**.

    a. Type the key name.

    b. Type the key value.

8. Click **[!UICONTROL Confirm]** and then **[!UICONTROL  Save]**.

## Edit a POI

1. Log into Places using your Adobe ID.
1. Log into Adobe Places Service using your Adobe ID.
1. In the top right side, click the icon that looks like a bulleted list.
1. Locate the POI that you want to edit.
1. Click **[!UICONTROL ...]** and select **[!UICONTROL View Details]**.
1. Update the information and click **[!UICONTROL Save]**.

## Delete a POI

1. Log into Places using your Adobe ID.
1. Log into Adobe Places Service using your Adobe ID.
1. In the top right side, click the icon that looks like a bulleted list.
1. Locate the POI that you want to delete.
1. Click **[!UICONTROL ...]** and select **[!UICONTROL Delete]**.

## Filter POIs by city, state, country, or metadata

1. Log into Adobe Places Service using your Adobe ID.
1. In the top right side, click the filtering icon.
1. You can filter POIs in one of the following ways: 

   * By library:

      a. Select a library.

   * By property:

      a. In Property drop-down list, select **[!UICONTROL Country]**, **[!UICONTROL State]**, or **[!UICONTROL City]**.
    
      b. In the next line, enter a value. 

        For example, you can select **[!UICONTROL State]** and type **[!UICONTROL California]**.

   * With metadata:

      a. Enter a key and value.

